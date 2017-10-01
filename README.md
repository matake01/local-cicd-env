![Payer Logotype](http://payer.se/public/PAYER_SUSTAINABLE_PAYMENTS_LOGO.png)
# Payer Autonomous & CI Environment

This is a base line environment for Autonomous Testing and Continuous Integration using Jenkins and the agile project management tool JIRA.

Get started by enter following command form your prompt:

```sh
docker-compose down && docker-compose build && docker-compose up -d
```

## Prerequisites

- [Docker Engine](http://www.docker.com)

## Docker Images

- JIRA Server
- JIRA MySQL
- Jenkins
- Docker Registry Server
- Docker Registry Web UI
- HAProxy

## Setup links

You may configure your setup in a way which enables communication and synchronization between one or more containers.

Example you can install following plugins in JIRA to be able to sync with your CI Build server and Git repository:

- [Jenkins Integration for JIRA](https://marketplace.atlassian.com/plugins/com.marvelution.jira.plugins.jenkins/server/overview)
- [Git Integration for JIRA](https://marketplace.atlassian.com/plugins/com.xiplink.jira.git.jira_git_plugin/cloud/overview)

#### Access from browser

After you've started the environment by docker-compose you should be able to access the specific service in the browser by;

```sh
http://localhost:<PORT>
```

##### Host service ports
- Jenkins: 49001
- JIRA UI: 49002
- Docker Registry UI: 8000

#### Force recreate all

```sh
docker-compose down && docker-compose build && docker-compose up -d --force-recreate
```

#### Rebuild a specific image

```sh
docker-compose down && docker-compose build && docker-compose up -d --build <CONTAINER_NAME>
```
