sed 's/^/Line /'
means:
s → substitute
^ → start of each line
Line → text to add

summary > "$file"
If the file doesn’t exist, Bash automatically creates it
If it exists, it gets overwritten
So > already handles file creation. no need to use touch

wc -l "$log_file"
This prints the line count + filename.
If you want just the number:
wc -l < "$log_file"

##  Bash Scripting Challenge: Log Analyzer and Report Generator
```bash

#!/bin/bash
log_file=$1
usage_display() {
        echo "Usage : Plesae enter the log_file path"
        echo "./filename.sh <log_file path>"
}

if [ $# -eq 0 ]
then
        usage_display
        exit 1
fi

if [ ! -f "$log_file" ]
then
        echo "Error : Log File does not exists"
        exit 1
fi

count(){
        error_count=$(grep -cE "ALERT | error" "$log_file")
        echo "Total Count : $error_count"
}

print_line_number() {
        echo "--------Critical Alerts-------"
        grep -n "ALERT" "$log_file" | sed 's/^/Line /' | tail -7

}

top_messages(){
        echo "---------Top 5 Error Messages-------"
        grep "ALERT" "$log_file" | awk '{$1=$2=$3=""; print}' | sort | uniq -c | sort -rn | head -5

}
summary() {
        echo "---------SUMMARY REPORT-----------"
        analysis_date=$(date '+%Y-%m-%d')
        echo "Analysis Date : $analysis_date"
        echo "Log File : $log_file"
        total_lines=$(wc -l < "$log_file")
        echo "Total Lines Processed : "$total_lines""
        count
        top_messages
        print_line_number

}
report() {
        file="log_report_$(date '+%Y-%m-%d').txt"
        summary | tee "$file"
}

archive() {
        if [ ! -d "archive" ]; then
                mkdir archive
        fi
        mv "$log_file" archive/
        if [ $? -eq 0 ]; then
                echo "Confirmation message : Log File moved successfully"
        fi
}
report
archive
```

## What you learned (3 key points)
- Report Generation
- Concept of grep and awk
- log file management and extraction of data

                     
                                                                                                                                          1,1           Top
