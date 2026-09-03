### Task 1: Understand workflow_call

#### Before writing any code, research and answer in your notes:

1. What is a reusable workflow?
   - It is a YAML formatted file, which are very similar to normal workflow file.
   - As with other workflow files, you locate reusable workflows in the .github/workflows directory of a repository.
   - Subdirectories of the workflows directory are not supported.

2. What is the workflow_call trigger?
   on:
     workflow_call:
   The file must include the workflow_call trigger under the on key to be recognized as reusable.
   
4. How is calling a reusable workflow different from using a regular action (uses:)?
   It is different in a sense that a reuable workflow will be called directly within the job,
   as compared to actions, which are called from within the steps.
    
5. Where must a reusable workflow file live?
   The recommended approach is that it should live inside the same .github/workflows.

#### Your reusable workflow and caller workflow YAML

```
name: Reusable Build

on:
    workflow_call:
        inputs:
            app-name:
                type: string
                required: true
            environment:
                type: string
                required: true
                default: staging
        secrets:
            docker_token:
                required: true
        outputs:
            build_ver:
                description: "The Version Variable output"
                value: ${{ jobs.set_outputs.outputs.version }}
        

jobs:
    code:
        runs-on: ubuntu-latest
        steps:
            - name: Checkout Code
              uses: actions/checkout@v6

            - name: Prints Building <app_name> for <environment>
              run: echo "Building ${{ inputs.app-name}} for ${{ inputs.environment}}"

            - name: Prints Docker Token
              run: echo "Docker token is set - ${{ secrets.docker_token }}"

    
    set_outputs:
        runs-on: ubuntu-latest
        outputs: 
            version: ${{ steps.ver-id.outputs.ver }}
        steps:
            - name: Build Version
              id: ver-id
              run: |
                sha=${GITHUB_SHA:0:7}
                echo "ver=v1.0@$sha" >> "$GITHUB_OUTPUT"

```

```
name: Caller Workflow

on: 
    push:
        branches: [main]

jobs:
    build:
        uses: ./.github/workflows/reusable-build.yml
        with: 
            app-name: "my-web-app"
            environment: "Production"
        secrets:
            docker_token: ${{ secrets.DOCKER_TOKEN }}

    read_output:
        runs-on: ubuntu-latest
        needs: build
        steps:
            - name: Prints the output
              run: echo "${{ needs.build.outputs.build_ver }}"

```
#### Your composite action YAML

```
name: 'Greetings Action'
description: "Greet In a local Languague"
inputs:
  name:
    required: true
  language:
    default: en
outputs:
  greeted:
    description: "An Output Result"
    value: ${{ steps.out-id.outputs.greeted }}

runs:
  using: "composite"
  steps:
    - name: Print Greeting
      run: echo "Hello in Languauge ${{ inputs.language }}"
      shell: bash
      
    - name: Print OS Version
      run: | 
        date
        lsb_release -a
      shell: bash

    - name: Print outputs
      id: out-id
      run: echo "greeted=true" >> "$GITHUB_OUTPUT" 
      shell: bash

```

```
name: Custom Action Workflow

on: workflow_dispatch

jobs:
    action-build:
        runs-on: ubuntu-latest
        steps:
            - name: Action Checkout
              uses: actions/checkout@v6

            - name: Use Composite Action
              id: greet-step
              uses: ./.github/actions/setup-and-greet
              with:
                name: Hina
                language: Spanish

            - name: Print Greet value
              run: echo "Greet variable value is ${{ steps.greet-step.outputs.greeted }}"
```

#### The comparison table from Task 6
Fill this in your notes:

                            Reusable Workflow	  Composite Action
Triggered by	              workflow_call	     uses: in a step
Can contain jobs?	               Yes                   No
Can contain multiple steps?	   No                   Yes
Lives where?	              .github/workflows       .github/actions/...
Can accept secrets directly?	   Yes                     No
Best for                      share a whole pipeline   share a step sequence.

#### Screenshot of the caller workflow triggering the reusable one
<img width="1007" height="362" alt="image" src="https://github.com/user-attachments/assets/c56e4e92-f09c-469f-b86f-2d4b1ba51196" />

