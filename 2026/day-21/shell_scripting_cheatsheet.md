## Task 1: Basics

      1. Shebang (#!/bin/bash) — what it does and why it matters
         Tells the interpreter version so that portability doesn't becomes an isuue
      2. Running a script — chmod +x, ./script.sh, bash script.sh
         Giving Executable permission to files
      3. Comments — single line (#) and inline
         (#) single line comment, <<disclaimer disclaimer ---- multiline comment
      4. Variables — declaring, using, and quoting ($VAR, "$VAR", '$VAR')
         name="hina" => echo "my Name is "$name""
      5. Reading user input — read
         read -p "Enter your designation" designation
      6. Command-line arguments — $0, $1, $#, $@, $?
         - `$0` → script name
         - `$#` → number of arguments
         - `$@` → all arguments
         - `$?` → exit status of previous command

## Task 2: Operators and Conditionals

      1. String comparisons  =, !=, -z, -n
         -z → true if the string is empty (zero length)
         -n → true if the string is not empty (non-zero length)
      2. Integer comparisons — -eq, -ne, -lt, -gt, -le, -ge
         -eq --- equal to
         -ne --- not equal to
         -lt --- less than
         -gt --- greater than
         -le --- less than and equal to
         -ge --- greater than and eual to
      3. File test operators — -f, -d, -e, -r, -w, -x, -s
         -f --- Checks if the file is a regular file
         -d --- checks if directory exists
         -e --- checks if fike exists
         -s --- checks if file is not empty
         -r --- if file has read permission
         -w --- if file has write permission
         -x --- if file has execute permission
      4. if, elif, else syntax
         if [ -f "$filename" ]; then echo "File exists" else echo "file does not exists"
         fi
      5. Logical operators — &&, ||, !
      6. Case statements — case ... esac

## Task 3: Loops

      1. for loop — list-based and C-style
         ````bash
         for car in bmw opel VW mecedes;
         do
           echo "$car"
         done
         for ((i; i>=10; i++)); do
           echo "$i"
         done
      2. while loop
         i=0
         while (( i<=10 ))
         do
           echo "$i"
           ((i++))
         done
         
         i=0
        while [ "$i" -le 10 ]
        do
            echo "$i"
            ((i++))
        done
        
      3. Until loop
         Until loops are similar to while loops, but they execute until a specified condition becomes true.
        count=1
        until [ $count -gt 5 ]; do
          echo "Count is $count"
          ((count++))
        done
        
      4. Loop control — break, continue
      
      5. Looping over files — for file in *.log
         for [ $file in *.log ]
         do
           echo "The file name is "$file""
         done
         
      6. Looping over command output — while read line
         command | while read -r line; do
          echo "$line"
      done
      read -r prevents backslash escaping issues.
         ````

## Task 4: Functions

      1. Defining a function 
        function_name() { ... }
      2. Calling a function
         function_name
      3. Passing arguments to functions — $1, $2 inside functions
        function_name <argument>
      4. Return values — return vs echo
        echo --- print or returns actual values or data
        return --- return in Bash functions only returns an exit status (0–255), not actual values.
      5. Local variables —
        local <variable_name>

## Task 5: Text Processing Commands

      1. grep — search patterns, 
      -i, Search ignoring case differences (uppercase or lowercase)
      -r, Search through all files in a directory and its subdirectories
      -c, count
      -n, line number --- Prefix each line of output with the 1-based line number within its input file.
      -v, Find lines that do not match the pattern
      -E, enables Extended Regular Expressions (ERE), so you can use patterns like +, ?, |, and () without escaping them.
      
      2. awk — print columns, field separator, patterns, BEGIN/END
      3. sed — substitution,
         delete lines, sed '/pattern/d' file ----- (d = delete matching lines)
         in-place edit, sed -i 's/old/new/' file----(-i modifies the file directly)
         
      4.cut — extract columns by delimiter
      -d - Choose what separates the fields
      -f - Select specific fields to display
      --complement - Show all fields except the selected ones
      
      5. sort — 
      alphabetical, by default 
      numerical, -n
      reverse, -r
      unique, -u
      
      6. uniq — deduplicate, 
      count duplicates, -c
      7. tr — translate/delete characters
      8. wc — line/word/char count
         wc -l
      9. head / tail — first/last N lines, follow mode
      
## Task 6: Useful Patterns and One-Liners

Include at least 5 real-world one-liners you find useful. Examples:
1. Find and delete files older than N days
    find <path> -type f -name ".*gz" -mtime +30 -delete 
2. Count lines in all .log files
    wc l ".*log"
3. Check if a service is running
    systemctl is-enabled / is-active nginx
4. Monitor disk usage with alerts
      usage=$(df / | awk 'NR==2 {print $5}' | tr -d '%')
  if [ "$usage" -gt 80 ]; then
    echo "ALERT: Disk usage exceeded 80%"
  fi
5. Parse CSV or JSON from command line
6. Replace a string across multiple files
7. Tail a log and filter for errors in real time
    tail -f logfile.log | grep --line-buffered "ERROR"
      tail -f → follows the log in real time
      grep → filters only lines containing "ERROR"
      --line-buffered → shows matches immediately without delay

## Task 7: Error Handling and Debugging

      Document with examples:
      1. Exit codes — $?, exit 0, exit 1
          $? ---- caputers the output of above command
          exit 1 ---- General errors, Miscellaneous errors
          exit 0 ---- Success
      2. set -e — exit on error
      3. set -u — treat unset variables as error
      4. set -o pipefail — catch errors in pipes
      5. set -x — debug mode (trace execution)
      6. Trap — trap 'cleanup' EXIT
          ````bash
      #!/bin/bash
      set -euo pipefail
      #mkdir scripts || echo "Folder exists" (|| with this, error is handled explicitly and 
      set -o pipefail will not work and script will continue running)
      
      mkdir scripts
      echo $name
      ````
      
        
      
