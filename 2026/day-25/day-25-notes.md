## Task 4: Branching Strategies

### Research the following branching strategies and document each in your notes with:

  How it works (short description)
  A simple diagram or flow (text-based is fine)
  When/where it's used
  Pros and cons
  
  GitFlow — develop, feature, release, hotfix branches
  GitHub Flow — simple, single main branch + feature branches
  Trunk-Based Development — everyone commits to main, short-lived branches
  
  #### Answer:
  1. Which strategy would you use for a startup shipping fast?
     Github Flow. Because it has simple structure of main branch with sub branches being created for features,
     pull requests are then made and after reviewing the requests, commits are merged into main ensuring fast shipping.
     
  2. Which strategy would you use for a large team with scheduled releases?
     GitFlow because it used for scheduled releases, has structured branches for development, testing,
     production and releases of product is monthly, quaterly or yearly.
     
| Strategy    |         Branches |  Complexity | Best for                     |
| ----------- | ---------------: | ----------: | ---------------------------- |
| GitFlow     |    Many branches |        High | Versioned releases           |
| GitHub Flow |     Few branches |         Low | Small teams, web apps        |
| Trunk-Based | Almost only main | Medium/High | Fast DevOps teams with CI/CD |
