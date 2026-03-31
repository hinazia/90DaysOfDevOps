**Scenario 2: High CPU Usage**
Your manager reports that the application server is slow.
You SSH into the server. What commands would you run to identify
which process is using high CPU?

Step 1: htop
Why: Will show live CPU Usage

Step 2: ps aux --sort=-%cpu | head -n 5
Why: Showed the top 5 processes, consuming highest CPU usage with PIDs

Step 3: Note PID
2070

**Scenario 3: Finding Service Logs**
A developer asks: "Where are the logs for the 'docker' service?"
The service is managed by systemd.
What commands would you use?

Step 1 : systemctl status docker
Why : to check the service

Step 2: journelctl -u docker
Why: Shows Docker Logs

Step 3: journelctl -u docker | head / tail -n 10
Why: Displays first or last 10 logs

Step 4: journelctl -u docker -f(to follow logs in real time)
Why : Displayed the live logs.


**Scenario 4: File Permissions Issue**
A script at /home/user/backup.sh is not executing.
When you run it: ./backup.sh
You get: "Permission denied"
What commands would you use to fix this?

Step 1 : ls -l /home/user/backup.sh
Why : Check current permission
Look for: -rw-r--r-- (notice no 'x' = not executable)

Step 2: chmod +x /home/user/backup.sh
Why: Give execute permisiion to this path 

Step 3: Verify ls -l /home/user/backup.sh
Why: Look for: -rwxr-xr-x (notice 'x' = executable)

Step 3: Try running again ./backup.sh
Why : It will run because now it ha sthe permisiion


