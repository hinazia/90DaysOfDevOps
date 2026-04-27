## Process commands / Service commands/ Log commands / One service on your system WorkFlow

### Example 01

                  Commands .................... Outputs

                  sudo systemctle start nginx .... it started
                  systemctl status nginx ....... status was shown
                  pgrep nginx................... PID of ngnix
                  sudo strace -p 608 ............ ubuntu@ip-172-31-43-236:~$ sudo strace -p 608
                                                                             strace: Process 608 attached
                                                                             epoll_wait(9,  
                                                                             (That output means cron is just sitting idle — waiting for the next job to trigger.)
                  journalctl -u nginx .......... no entries (because nginx spelling was wrong. Logs were shown once spelling was corrected)
                

### Example 02

ubuntu@ip-172-31-43-236:~$ top | grep nginx (no output, does not work)
ubuntu@ip-172-31-43-236:~$ ps aux | grep nginx
root         599  0.0  0.1  11168  1736 ?        Ss   20:28   0:00 nginx: master process /usr/sbin/nginx -g daemon on; master_process on;
www-data     608  0.0  0.5  12892  5024 ?        S    20:28   0:00 nginx: worker process
www-data     609  0.0  0.5  12892  4676 ?        S    20:28   0:00 nginx: worker process
ubuntu      2052  0.0  0.2   7084  2204 pts/0    S+   21:23   0:00 grep --color=auto nginx
ubuntu@ip-172-31-43-236:~$ htop | grep nginx ((no output, does not work))

### Example 03

ubuntu@ip-172-31-43-236:~$ tail -n 2 /etc/passwd
hina:x:1003:1003::/home/hina:/usr/bin/bash
dnsmasq:x:999:65534:dnsmasq:/var/lib/misc:/usr/sbin/nologin

ubuntu@ip-172-31-43-236:~$ head -n 2 /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
    
