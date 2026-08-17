- Write in your notes: What is a GitHub-hosted runner? Who manages it?
  
  The runners are the servers/machines that executes your jobs in Github Action Workflows.  
  The GitHub-hosted runner is provided by the Github itself and is also managed by them.

- Why does it matter that runners come with tools pre-installed?
  
  It helps with the quick execution of workflows without the headache of configuring network, OS and image settings.

- Why are labels useful when you have multiple self-hosted runners?

  It helps to identify which runner to use in workflows. You might have 3 linux runners running.
  Labels will help you to identify them.

  ### Task 6: GitHub-Hosted vs Self-Hosted
  
  #### Fill this in your notes:

| Feature                 | GitHub-Hosted                                                                                                  | Self-Hosted                                                                                              |
| ----------------------- | -------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| **Who manages it**      | GitHub                                                                                                         | You / your organization                                                                                  |
| **Cost**                | Free for public repositories; private repositories have included minutes and may incur charges after the quota | GitHub does not charge for the self-hosted runner itself, but **you pay for the machine/infrastructure** |
| **Pre-installed tools** | Yes, many common tools and software are pre-installed                                                          | No — you install and maintain the tools you need                                                         |
| **Good for**            | Learning, personal projects, and most CI/CD workflows                                                          | Organizations needing custom environments, hardware, networking, or more control                         |
| **Security concern**    | GitHub manages the runner environment and standard runners are fresh VMs for most jobs                         | **Higher responsibility** — you are responsible for securing and maintaining the runner                  |
