## Task 1: Git Merge — Hands-On

3. Observe the merge — did Git do a fast-forward merge or a merge commit?
   Git did fast-forward merge
5. Merge feature-signup into main — what happens this time?
   Git did Merge commit
   
#### Answer in your notes:

1. What is a fast-forward merge?
  - A fast-forward merge in Git is a type of merge operation that occurs when the target branch (usually main or master) has no new commits
    since the feature branch was created. Instead of creating a merge commit, Git simply moves the branch pointer forward to point to the
    latest commit on the feature branch, creating a linear history.
2. When does Git create a merge commit instead?
  - If you've been working on a branch while the main branch has moved forward with new changes, Git can't fast-forward—this is when a merge commit is necessary.
    A merge commit creates a new point in the project history that records the combination of changes from both branches.
3. What is a merge conflict? (try creating one intentionally by editing the same line in both branches)
  - Two people changing the same file/same line number in different branches at the same time and commiting there changes, so conflict occurs

## Task 2: Git Rebase — Hands-On

#### Answer in your notes:

1. What does rebase actually do to your commits?
  -	Creates a one linear history of two different branches commit history
   
2. Why should you never rebase commits that have been pushed and shared with others?
 - When you rebase stuff, you’re abandoning existing commits and creating new ones that are similar but different. If you push commits somewhere and others 
  pull them down and base work on them, and then you rewrite those commits with git rebase and push them up again, your collaborators 
  will have to re-merge their work and things will get messy when you try to pull their work back into yours.

3. When would you use rebase vs merge?
 - When you have to sequence the commit history of two branches, use rebase
   Merge is used when we are just adding the commits of one branch to another

## Task 3: Squash Commit vs Merge Commit

#### Answer in your notes:

1. What does squash merging do?
  - Squash the multiple commits into neat commit

2. When would you use squash merge vs regular merge?
  - When we want to combine multiple commit messages into one commit message.
  - Regular Merge is adding commits of one branch into another

3. What is the trade-off of squashing?
  - All the commits are combined into one and there will be no commit history to trace back to and
    so detailed commit history (small changes and progression) is lost

## Task 4: Git Stash — Hands-On

#### Answer in your notes:

1. What is the difference between git stash pop and git stash apply?
  - git stash pop : stashes ki reference ki copies save nahi rakhta and space bhi isse save hoti hai
  - git stash apply : a reference copy of stash is saved and then a stack of stashes is created and popping becomes difficult
    
2. When would you use stash in a real-world workflow?
  - scenerio : tester asked a developer to quickly fix a bug in another file in another branch,
    so I stash (keeping it aside) my work, fixed tge bug, stash pop and will resume my work.
    
## Task 5: Cherry Picking

#### Answer in your notes:

1. What does cherry-pick do?
  - Pick the specific commit which is needed (picking only the top cheer not the whole cake)
    
2. When would you use cherry-pick in a real project?
  - When we have different multiple features/commits eg login, signup and we want only one specific commit/feature in other branch
    
3. What can go wrong with cherry-picking?
   - cherry picking the commits which are dependent on other commits. an error will be thrown as shown below
   - Solution : try to pick the independent small commits or cherry pick the whole range
     <img width="973" height="186" alt="image" src="https://github.com/user-attachments/assets/795bfed4-d202-4f36-bb3e-1d3827501b4c" />


