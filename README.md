# Local CI/CD env

A local lab environment for CI/CD including Jira, Jenkins and a self-hosted Docker Registry.

## Prerequisites

- [Docker Engine](http://www.docker.com)

## Includes
- JIRA Server
- JIRA MySQL
- Jenkins
- Docker Registry Server
- Docker Registry Web UI
- HAProxy

## Recommended plugins
- [Jenkins Integration for JIRA](https://marketplace.atlassian.com/plugins/com.marvelution.jira.plugins.jenkins/server/overview)
- [Git Integration for JIRA](https://marketplace.atlassian.com/plugins/com.xiplink.jira.git.jira_git_plugin/cloud/overview)

## Run environment

Start containers from project root:

```sh
docker-compose up -d
```

Now available in your browser:

```sh
http://localhost:<PORT>
```

### Host service ports
- Jenkins: 49001
- JIRA UI: 49002
- Docker Registry UI: 8000
