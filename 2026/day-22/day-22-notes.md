## Understand the Git Workflow

Answer these questions in your own words

1. What is the difference between git add and git commit?
git add -------> Files go from Untracked status to Staged Status
git commit ----> Files go from Staged status to Tracked Status

2. What does the staging area do? Why doesn't Git just commit directly?
The staging area in Git lets you choose exactly which changes should go into the next commit. It acts like a “preview basket” before saving a snapshot.
Git doesn’t commit directly because you may edit many files but only want to commit some of them together in a clean, meaningful commit.

3. What information does git log show you?
It shows the commit history

4. What is the .git/ folder and what happens if you delete it?
It changes the normal folder into git repository. if the .git folder is deleted, the repository becomes a normal folder 

5. What is the difference between a working directory, staging area, and repository?
Working directory: The actual files/folders on your computer where you make changes (tracked and untracked files).
Staging area: The place where you prepare selected changes before committing (git add puts changes here).
Repository: The Git database/project history where committed snapshots are permanently stored
