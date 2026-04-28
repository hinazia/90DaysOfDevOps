## Task 1: Basic Functions 
#!/bin/bash
greet() {

        echo "Hello $1!"
}
greet Hina

add() {
        echo "Addition of Two Numbers"
        sum=$(( $1 + $2 )) (Airthmatic Expressions in bash)
        echo $sum
}
add 3 5

## Task 2: Functions with Return Values
#!/bin/bash
check_disk() {
        df -h
}
check_memory() {
        free -h
}
disk_check() {
        echo "Disk Health Check"
        echo "Disk Usage"
        check_disk
        echo "Free memory"
        check_memory
}
disk_check

## Task 3: Strict Mode — set -euo pipefail
#!/bin/bash
set -euo pipefail
#echo $name

#mkdir scripts || echo "Folder exists" (|| with this, error is handled explicitly and 
set -o pipefail will not work and script will continue running)

mkdir scripts
echo $name

### Document: What does each flag do?
set -e → mkdir: cannot create directory ‘scripts’: File exists
set -u →  name: unbound variable 
set -o pipefail → mkdir: cannot create directory ‘scripts’: File exists (Pipeline fails)

Without pipefail ---> Script Continues, code continues
With pipefail -----> Script exits properly, error handling in bash

## Task 4: Local Variables
#!/bin/bash
local_func() {
        local name="Hina"
        echo $name

}

func() {
        job="Student"
        echo $job
}
local_func ----> Hina
func ----------> Student
echo $name -----> no output
echo $job -------> Student
Without local keyword, variables have global scope in bash 

## Task 5: Build a Script — System Info Reporter
#!/bin/bash
set -euo pipefail
info() {
        hostname
        cat /etc/os-release
        printf "\n"
}
up_time() {
        echo -e "-----UPTIME----- \n"
        uptime -p
}
disk_usage() {
        echo -e "----DISK USAGE----- \n"
        df -h | head -5
}
mem_usage() {
        echo -e "----MEMORY USAGE---- \n"
        free -h
}
cpu_process() {
        echo -e "------CPU PROCESSES----- \n"
        ps aux --sort=-%cpu | head -5
}
main() {
        echo -e "=======SYSTEM INFO REPORTER========= \n"
        info
        up_time
        disk_usage
        mem_usage
        cpu_process
}

### What I learned (3 key points)
- Without Local keyword, variables have global scope in functions
- Error handling in Bash Script and pipeline fails
- How to write Airthmatic expressions in Bash
