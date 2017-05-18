---
layout: classic-docs
title: “Build a Project”
short-title: “Build a Project”
description: “First project build on CircleCI 2.0"
categories: [getting-started]
order: 4
---

## Build a Project 

This document describes how to configure your project to run on CircleCI 2.0. 

### Prerequisites

- Complete the steps in the [Join Beta & Sign Up]({{ site.baseurl }}/2.0/sign-up/) document. 
- Install and start Docker, see [the Docker store](https://store.docker.com/search?offering=community&type=edition) for a free download that is compatible with your operating system. 
- Use the `docker pull circleci/<language>` command to download a build image for your language, see [the CircleCI repo on hub.docker.com](https://hub.docker.com/u/circleci/) for a complete list of images.

### Steps

1. Create a directory called `.circleci` in the root directory of your local GitHub or Bitbucket code repository. 

2. Create a `config.yml` file in the `.circleci` directory with the following lines, replacing *project root directory* with your project directory and *language:version* with your programming language and version number. 

```YAML
version: 2
jobs:
  build:
    working_directory: ~/<project root directory>
    docker:
      - image: <language>:<version>
    steps:
      - checkout
      - run: echo "hello world"
```

The image defines the execution environment for your build. The step checks out the code in the project directory and runs the `echo` command.

3. Commit and push the changes.

4. Go to the [Add Projects](https://circleci.com/add-projects) page in CircleCI and click the Build Project button next to your project.

CircleCI 2.0 checks out your code, echoes "Hello World", and posts a green build! If the build fails, you are notified in email of the failure with a log of the failing command, exit code, and output.
