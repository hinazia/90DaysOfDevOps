## Task 1 and 2 : For and While Loop
  ### Loops through a list of 5 fruits
  #!/bin/bash
  fruits=(apple banana grapes cheery pineapple)
  for fruit in ${fruits[@]}; do
          echo $fruit
  done
  ### Prints numbers 1 to 10 using a for loop
  count=1
  while [ $count -le 10 ]; do
          echo "Count is : $count"
          ((count++))
  done  
  ### Counts down to 0 using a while loop
  read -p "Enter the Number : " NUM
  while [ $NUM -ge 0 ]; do
          echo $NUM
          ((NUM--))
  done
  echo "Done"

## Task 3: Command-Line Arguments
### Create greet.sh that:
#!/bin/bash
if [ $# -eq 0 ]
then
        echo "Usage:./greet.sh"
        exit 1
fi
echo "Hello $1"

### Create args_demo.sh that:
#!/bin/bash
echo "Hellooo $1 $2 $3"
echo "Total Number of Arguments : $#"
echo "Print the value of Arguments : $@"
echo "Prints the Script Name : $0"

## Task 4: Install Packages via Script
if [ "$EUID" -ne 0 ]; then echo "Run as root"; exit 1; fi (error handling, EEffective User ID, automatically set by bash to run the script as Root)
(Then we dont have to use sudo)
packages=(nginx curl wget)
for package in "${packages[@]}"
do
        if sudo dpkg -s $package &> /dev/null ; then
                echo "$package is Installed"
        else
                sudo apt install "$package" -y
        fi
done
systemctl is-active (--quiet nginx ---- use to redirect output in black hole)
command -v curl wget (&> /dev/null ---- use to redirect output in black hole)

## Task 5: Error Handling
#!/bin/bash
set -e
mkdir /tmp/devops-test || echo "directory already exists" (either set e or || statement for error handling. Both acnnot be used together)
touch /tmp/file1.txt

## What you learned (3 key points)
- Arguments and their application
- Error handling in shell script
- Variables in quotes to avoid code breaking eg package="My Package", the value of package can be treated as two arguments instead of one word
- Output Redirecting
  
