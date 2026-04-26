### Document: What happens if you remove the shebang line?
   It ensures that the correct version of interpretor is used. example Bash(Ubuntu), zsh(Mac), corn etc

### Try using single quotes vs double quotes — what's the difference?
    In double quotes, we can input variables and in single quotes, variables are treated as strings(like no variable can be used). 

## Task 4: If-Else Conditions
### Create check_number.sh that:

  read -p "Enter File Name to be checked : " filename

if [ -f "$filename" ]; then
        echo "File exists"
else
        echo "file does not exists"

fi

## Task 5: Combine It All
### Create server_check.sh that:

  #!/bin/bash

read -p "Enter the Service name : " SERVICE

read -p "Do you want to check the status : Answer y or n" ANS

if [ $ANS == "y" ]; then
        sudo systemctl status $SERVICE

        if systemctl is-active --quiet "$SERVICE"; then (--quiet suppresses output, so you can control what gets printed.)
                echo "$SERVICE is active"
        else
                echo "$SERVICE not active"
        fi

elif [ $ANS == "n" ]; then
        echo "Skipped"

else
        exit 1
fi
