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
