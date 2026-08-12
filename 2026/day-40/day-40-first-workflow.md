### Task 3: Understand the Anatomy

Look at your workflow file and write in your notes what each key does:

  on: It is a trigger/condition to run the workflow
  jobs: what is needed to run the workflow eg build, tests, deploy units
  runs-on: server where workflow will run eg linux, windows, mac
  steps: needed to get the job done
  uses: custom / prebuilt actions
  run: the command to excute t
  he steps
  name: (on a step), name given to steps

### Task 5: Break It On Purpose

Write in your notes: What does a failed pipeline look like? How do you read the error?

It will be exited with a code and a red X will appear with workflow failed status.

### WorkFlow

```
# This is workflow name
name: Hello

# workflow runs on a trigger
on:
  push:
    branches: [main]
      
jobs:
    greet: # This is Job name
        runs-on: ubuntu-latest # Job will run on this server given by Github for free
        steps:
            - name: action/checkout
              uses: actions/checkout@v6
            - name: Actions Greeting
              run: echo "Hello from GitHub Actions!"
            - name: Printing Info
              run: | 
                date
                ls 
                lsb_release -a
                echo ${{ github.ref_name }}

```
