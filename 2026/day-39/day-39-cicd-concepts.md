### Task 1: The Problem

Think about a team of 5 developers all pushing code to the same repo manually deploying to production.

Write in your notes:

##### What can go wrong?
  - Different OS bases eg developer's MAC and server is in LINUX.
  - Bugs in Production
  - Different deploment styles
  - Files missing, API's not working
  - Long Working hours, Customer Unhappy, Rushed deployments because of deadlines  

##### What does "it works on my machine" mean and why is it a real problem?
It is a real problem because the end goal is clients machine. They should be able to access it easily without any difficulty.
A product or a piece of code is useless if it works only on the developer machine.

##### How many times a day can a team safely deploy manually?
Maybe twice or thrice a day.

### Task 2: CI vs CD

Research and write short definitions (2-3 lines each):

##### Continuous Integration — what happens, how often, what it catches

  - This is the Collaboration Layer
  - Developer pulls the updated code, make changes to it and push
  - Automationation happends: It is being Built, Tested for bugs and goes into Production
  - This automation of the pipelines, helps detect the bugs early, ensures continuous develiry of updated code,
    Reduced merge conflicts (small, frequent changes) and smooth delivery/deployment of code.
  - Happens 200, 500 or 1000  times a day
    
##### Continuous Delivery — how it's different from CI, what "delivery" means

  - The Reliability Layer
  - The code integration is done, build, testing is done and code is ready for production
  - Now you have the production ready code for delivery. One-click deployments when business is ready
. 
##### Continuous Deployment — how it differs from Delivery, when teams use it

  - The Automation Dream
  - The code is continouly deployed in prodcution automatically
  - Comprehensive test coverage (>80% is ideal)
  - Robust monitoring in production
    
##### Write one real-world example for each.
  - Netflix example: 1,000+ daily deployments
  - Bnaking App for continuous delivery, just a check from the head before roll out
  - Startup Scenerio

### Task 4: Draw a Pipeline

Draw a CI/CD pipeline for this scenario:

A developer pushes code to GitHub. The app is tested, built into a Docker image, and deployed to a staging server. 

Code (Pushed) ------> Automated Testing ------> AUTOMATED Build (Docker) ------> Automated Staging to Deployment -------> Deployed/Delivered to (Client)

