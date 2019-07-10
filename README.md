# Local GoCD development setup

This repository contains a basic GoCD setup that you can run on your own laptop to try things out.

## Getting started

### Starting GoCD Server and Agent


This command starts a GoCD server and client:

```
$ docker-compose up --build
```

Wait for a few minutes for everything to start up. You will see a few errors on the terminal during this time. This is normal as agent and server are starting up at the same time and won't be able to talk to each other initially.

After a few minutes, you can reach the GoCD Server on http://localhost:8153

### Configuring your own config-repo

The primary way of configuring GoCD pipelines in code is through "Config Repositories". At startup, this is set to a dummy repository. To point GoCD to your own repository, go to ["Admin" -> "Config Repositories"](http://localhost:8153/go/admin/config_repos) and change the repository to your own.


### Installing additional tools on the GoCD Agent

You can add commands to install additional tooling in [`Dockerfile.gocd-agent`](./Dockerfile.gocd-agent)

### Get access to AWS on the GoCD Agent

The `docker-compose.yaml` is set up to forward your shells `AWS_*` environment variables to the container. For the agent to have access to AWS, simply `awsume` into your AWS account on the terminal before you call `docker-compose`

## Assignment

Build a GoCD pipeline that can deploy our beloved Todo-list application to AWS. These are the criteria you need to meet !
1. The pipeline should be configured via script file which resides in another repository.
2. The deployment should happen inside an agent.
3. Todo-list application should be up and running at `https://app-<your-aws-account-id>.s3-website-ap-southeast-1.amazonaws.com` after the pipeline finished running.

#### ** Out-of-scope **
We've provided these things for you
1. Terraform codes that responsible for creating S3 bucket.
2. Build script for generating static contents.
3. Deployment script for applying terraform codes to AWS.
4. Files-upload script for uploading static content from the generated folder to the S3 bucket.

Checkout https://github.com/gotham-learning/vue-gotham-todo's README.md for more information.
### Resources

1. Example of GoCD configuration script. (https://github.com/gotham-learning/gocd-pipeline-config)
2. Master Dean’s Todo-list application. (https://github.com/gotham-learning/vue-gotham-todo)

### Reminders

1. Please fork the provided repos to your git account before anything so that you can commit and push to trigger your pipeline.
2. In case you need to install additional software inside GoCD server or agent, you need to restart those containers.
3. Apart from the above criteria, you're free to design and develop in anyway you like. ENJOY.