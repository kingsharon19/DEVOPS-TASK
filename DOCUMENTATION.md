# DEVOPS-TASK
## Overview
The Say Hello workflow is designed to execute a simple bash script that prints a greeting message to the console. The workflow is triggered by a manual approval step and can be run on demand.

## Jobs
The workflow contains a single job named say-hello, which runs a bash script to print a greeting message. The job uses the circleci/node:14-browsers Docker image.

yaml
Copy code
jobs:
  say-hello:
    docker:
      - image: circleci/node:14-browsers
    steps:
      - run:
          name: Say Hello
          command: echo "Hello, World!"
## Workflows
The Say Hello workflow consists of a single job that runs the say-hello job. However, the job requires manual approval before it can be executed.

yaml
Copy code
workflows:
  version: 2
  say-hello-workflow:
    jobs:
      - say-hello
    approval:
      type: approval
      requires:
        - say-hello
When the workflow is run, the say-hello job is executed first. Once the job has completed, the workflow enters a pending state and waits for manual approval. The user can approve the workflow by clicking the Approve button in the CircleCI UI. Once approved, the workflow moves into a running state and executes the say-hello job again.

## Conclusion
This document provides an overview of the Say Hello workflow in CircleCI, which executes a simple bash script that prints a greeting message. The workflow is triggered by a manual approval step and can be run on demand.
