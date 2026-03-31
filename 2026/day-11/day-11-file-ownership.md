# Day 11 Challenge

## Files & Directories Created
   --> **Directories**                  **Files**
         app-logs/                       devops-file.txt, project-config.yaml
         heist-project/vault             gold.txt
         heist-project/plans             strategy.conf
         bank-heist/                     access-codes.txt, blueprints.pdf, escape-plan.txt

## Ownership Changes
[before/after for each file]
do the documentation after the task is completed

Example:
- devops-file.txt: user:user → tokyo:heist-team

## Commands Used
[your commands here]
# View ownership
ls -l filename
# Change owner only
sudo chown newowner filename
# Change group only
sudo chgrp newgroup filename
# Change both owner and group
sudo chown owner:group filename
# Recursive change (directories)
sudo chown -R owner:group directory/ , ls -lR
# Change only group with chown
sudo chown :groupname filename


## What I Learned
[3 key points about file ownership]
1. Difference between /directory and directory/
2. Document after the atsk is completed otherwise it will be messy to document
3. the new command at line 27 --- Recursive change


Document: What's the difference between owner and group?
Answer : Owner is the single user while Group is collection of users. 
