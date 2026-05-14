## Task 1: Understanding Branches

Answer these in your day-23-notes.md:

1. What is a branch in Git?
In Git, a branch is like a separate workspace where you can make changes and try new ideas without affecting the main project.

2. Why do we use branches instead of committing everything to main?
Main/Master branch is usually reserved for the production ready code. We use branches to make changes and try new ideas instead of messing up the 
main code/branch. Ik file ki multiple copies bananey se acha hai usko mutiple branches mei rakhdo like dev, testing, operations etc

3. What is HEAD in Git?
Currently cheezein kis branch mei hain. Pointout to the working branch. Points to Konsi branch mei konsa change/commit lastest hai

4. What happens to your files when you switch branches?
When you switch branches, Git updates your files to show the version saved in that branch.
So your files can change depending on the branch you move to or may have different versions in different branches.
like in Parallel universe

## Task 3: Push to GitHub
1. Answer in your notes: What is the difference between origin and upstream?
In Git:
origin → the remote repository URL name (usually my forked GitHub repo)
upstream → the branch or original repo you track for updates(sir shubhams repo)

Example:
You fork a repo from someone else
Your fork = origin
Original repo = upstream

## Task 4: Pull from GitHub
1. Answer in your notes: What is the difference between git fetch and git pull?
In Git:
git fetch : fetches the data from remote branch but do not mearge with the local working directory.
            - Use Git Fetch when you want to review updates from the remote repository without immediately merging them into your branch.
git pull : fetches the repo and immediately merges the remote repo with the local current working directory.
           Automatically attempts to merge changes, which can sometimes lead to conflicts.
           - Use git pull when you are sure of the updates in remote repo and wants them in your local repo

## Task 5: Clone vs Fork

Answer in your notes:

1. What is the difference between clone and fork?
- cloning is coping the repo from remote(Githup) to local(Git)
- forking is copying a repo in my Githup account to try new things
   
2. When would you clone vs fork?
remote to local - clone
fork is the pure Githup concept

3. After forking, how do you keep your fork in sync with the original repo?
You get an option to sync fork with the original. Rewiew the updates from the upstream and if okay click sync fork and boom

