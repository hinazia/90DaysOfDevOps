Find → filter → take action (compress / count / delete)
 - One-line understanding
find /path -name "*.log" -mtime +7 -exec gzip {} \;

Simple summary
-type f → only files
-name "*.log*" → match log files
-mtime +7 → older than 7 days
-exec gzip → compress them
| wc -l → count them
-delete → remove them

touch -d lets you set a file’s timestamp to a specific date/time instead of the current time.
It’s commonly used to simulate old/new files (e.g., touch -d "10 days ago" file.log) for testing.

## Task 1 : Log Rotation Code
#!/bin/bash
#
<<disclaimer
This script will take server backups and apply log rotation
so save space and automate the task
disclaimer

#read -p "Enter the logs Directory" log_dir

usage() {
        echo "./Usage <file.sh>  <Source Directory>"
}
if [ $# -eq 0 ]
then
        usage
        exit 1
fi
source_dir=$1

log_rotation() {
        echo "Take the logs from the given Directory"
        cp -a "$source_dir" /home/ubuntu/backup (-a = archive mode (preserves time, permissions, etc.))

        echo "Compress the File using the gzip"
        find /home/ubuntu/backup/ -type f -name "*.log*" -mtime +7 -exec gzip {} \;

        echo "Files older than 7 days count"
        find /home/ubuntu/backup -type f -mtime +7 |wc -l

        echo "Deleting the Files older than 30 days"
        find /home/ubuntu/backup -type f -name "*.gz" -mtime +30 -delete
}
log_rotation

## Task 2 : Server Backup
tar → archive tool
-c → create archive
-z → compress with gzip
-f → output file name follows
backup_${timestamp}.tar.gz → archive name
"$source_dir" → directory being archived

- 2>&1 = “send errors to wherever output is going”
  
#!/bin/bash
source_dir=$1
backup_dir=$2
timestamp=$(date '+%Y-%m-%d-%H') (with -%H, backup will be created hourly)
if [ ! -d "$source_dir" ]
then
        echo "Usage : Enter the Source and Backup Directory"
fi

create_backup() {
        tar -czf "$backup_dir"/backup_${timestamp}.tar.gz "$source_dir" &> /dev/null

        if [ $? -eq 0 ]; then
                echo "Backup Generated Successfully"
        fi
}
archive_info() {
        file="$backup_dir"/backup_${timestamp}.tar.gz
        echo "Name : $(basename "$file")"
        echo "Size : $(stat -c%s "$file") bytes"
}

delete_archive() {
         find "$backup_dir" -type f -name "*.tar.gz" -mtime +30 -delete
         if [ $? -ne 0 ];then
                echo "Archive Deleted Successfully"
        else
                exit 1
         fi
}
create_backup
archive_info
delete_archive

## Task 3: Crontab
Write cron entries (in your markdown, don't apply if unsure) for:
  - Run log_rotate.sh every day at 2 AM
    0 2 * * *
  - Run backup.sh every Sunday at 3 AM
    0 3 * * 7
  - Run a health check script every 5 minutes
    */5 * * *

## Task 4 : Combine — Scheduled Maintenance Script
#!/bin/bash
source log_rotate.sh
source server_backup.sh

log_output(){

        backup_output=$(create_backup)
        echo "$(date): $backup_output" | sudo tee -a /var/log/maintenance.log (to write in files in root directory)

        log_output=$(log_rotation)
        echo "$(date): "$log_output"" | sudo tee -a /var/log/maintenance.log

}
log_output
<img width="1111" height="65" alt="cron_job" src="https://github.com/user-attachments/assets/1c203ff1-6b34-4105-b681-e0d50dd2ac34" />


## What you learned (3 key points)
- Taking File backups
- Managing logs
- Writing in Root Directory files eg /var/log/maintenance.log
- Scheduling Tasks
