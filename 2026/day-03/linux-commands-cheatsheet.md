## Environment basics (2): 
uname -------> Linux, prints system info, kernel name etc (-a gives detailed info)
hostname ----> Shows ip address of machine 
lsb_release -a (or cat /etc/os-release) ---> (Linux Standard Base) information about your Linux distribution, such as version, release, codename

## Process management
top  -----> Display Linux Processes
htop -----> Shows live CPU usage, memory, running processes
ps   -----> report the snapshot of the current processes
ps aux --sort%-cpu | head -3 -----> sorts the processes by highest CPU usage

## FileSystem
mkdir ---->  create Directory
touch -----> create file
vim -------> create file and opens it in Vim editor
rm -rfv --------> remove files
ls --------> Lists files and folders ---> -l (lists all files folders), -a (lists the hidden . files and folders also)
cp -rfv <source> <destination>--------> copy file
stat <filename> -----> gives the file info
## Networking troubleshooting
ss ----> utility to investigate sockets
-t → TCP sockets
-u → UDP sockets
-l → listening sockets
-p → show process using the socket
-n → show numeric addresses/ports (no DNS resolution)
curl -I <service-endpoint>/ping ---->  tranfer a URL

## Permissions
chmod +rwx <filename>  

## Disk I/O , Memory
free -h -----> available memory in human readable form
df -h -------> report filesystem Space usage in human readable form (Tells you how much space is used and available on a disk/partition)
du -sh <filename eg /var/log) -----> estimate file space usage(Tells you how much space a specific folder or file consumes)
iostat ------> Input Output statistics for devices and partitions, CPU Statistics
