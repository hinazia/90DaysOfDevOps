# Day 09 Challenge

## Users & Groups Created
- Users: tokyo, berlin, professor, nairobi
- Groups: developers, admins, project-team

## Group Assignments
tokyo → developers
berlin → developers + admins (both groups)
professor → admins
nairobi + tokyo -> project-team

## Directories Created
/opt/team-workspace ..... with 775 permission
/opt/dev-project    ...... with 755 permisiion  (rwxrwxr-x)

## Commands Used

User: useradd -m, passwd, usermod
Group: groupadd, gpasswd -M user1,user2,user3 groupname(multiple users in a group),
       gpasswd -aG group1,group2 usermane (user in multiple groups)
Permissions: chgrp, chmod
Test: sudo -u username path, ls -ld [path],

## What I Learned
. Addition of multiple groups. Proper use of -aG
. How to follow instructions properly
. Importence of proper documenation 
