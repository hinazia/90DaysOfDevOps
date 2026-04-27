## Core Components of Linux
   . The linux architecture works on the ASK model. hence the core components are
       -> Application layer ... The user layer
       -> Shell ............... The interactive terminal, where we write commands or interacte with the kernel
       -> Kernel ............... The OS of Linux
       -> Hardware ............. Devices

## Processes
    . Everything in Linux is a process. example creating a folder, copying files, checking logs etc
    . To manage the processes we use commands like systemctl, journalctl -u (to see log files), ps, htop etc
           -> systemctle status nginx or docker
           -> journalctl -u nginx
           -> htop ----- processes in real time like task manager
           -> ps aux --- shows processes states (ready, sleeping zombie etc)
           
## What systemd does and why it matters
      . Systemd is the first process that runs after Linux boot and is responsible for starting and managing all the services. its id is always 1 "PID 1"
        Manager of the everything that runs on the linux system.

## List 5 commands you would use daily
        -> mkdir
        -> whoami
        -> ls -l .... lists files/folders details 
        -> cd
        -> ping ---- pinging websites
        
        
