# react-github-actions

- I have created this repo to understand how multiple workflows work in a project.
- There are 3 workflows in this repo; one that completes all tasks in 1 job, 
one that complete all tasks by seperating them into 3 different jobs, 
one that is related to issues event (that is triggered when a new issue is created) 
and contains information about the github.event context.
- Jobs in workflows use the scripts which is defined in the package.json file to perform certain tasks, like below: 
```yaml
lint-job:
  ...
    run: npm run lint
test-job:
  ...
    run: npm run test
deploy-job:
  ...
    run: npm run build
```
- Nodejs environment setup is skipped knowingly in the workflow since the runner is "ubuntu-latest" which already has nodejs.
To see packages which are installed on runner: https://github.com/actions/runner-images/blob/main/images/linux/Ubuntu2204-Readme.md
- issues.yaml file echoes some metadata about the github.event context
```yaml
name: Handle issues
on: issues
jobs:
  ...
    run: echo "${{ toJSON(github.event) }}"
```
- The changes in project can be seen via commits.
