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
