# Dockers

Nothing but net to master both containerization and Jenkins and merge the two where each exhibits a strength.
- For example, a `Dockerfile` in many ways is very much like a `Jenkinsfile` as each can execute a build (test too, sytle checks, etc) and produce artifacts worthy of keeping including the console output when they run. 
  - If you're familiar with Docker's multi-stage image builds, you'll know how to easily incorporate a variety of "upstream" and "official" tool images like for `maven` or `dotnet` and string them together to build a pipeline within a `Dockerfile`.... anyways I think contemplating the similarities and differences between `Dockerfile` and `Jenkinsfile` is a worthwile exploration. 


## Dockers + Pipelines

- [Docker + Pipeline](https://www.jenkins.io/doc/book/pipeline/docker)
  - These two tools together are a formidable force for simplicity and yet flexibility in all sorts of complicated CI/CD pipeline scenarios.
- Official images
  - [jenkins/jenkins](https://github.com/jenkinsci/docker) Controller
  - [jenkins/inbound-agent](https://hub.docker.com/r/jenkins/inbound-agent/)
    - [Source](https://github.com/jenkinsci/docker-inbound-agent)
    - Deprecated, former repository (image) names: 
      - [jenkinsci/jnlp-slave](https://hub.docker.com/r/jenkinsci/jnlp-slave)
      - [jenkins/jnlp-slave](https://hub.docker.com/r/jenkins/jnlp-slave)
- Plugins
  - [Jenkins Cloud for Docker](https://github.com/jenkinsci/docker-plugin) for dynamic docker agents
  - TODO from below
- Source
  - https://github.com/jenkinsci?q=docker


## Docker + maven example
https://github.com/jenkinsci/pipeline-examples/blob/master/declarative-examples/jenkinsfile-examples/mavenDocker.groovy


## Plugin Installation Manager

- <https://github.com/jenkinsci/plugin-installation-manager-tool>
- In docker images, replaces [`install-plugins.sh`](https://github.com/jenkinsci/docker/blob/master/install-plugins.sh)
  - Port from `bash` to `java`  


## Plugins (TODO)

- https://github.com/jenkinsci/docker-commons-plugin
- https://github.com/jenkinsci/docker-workflow-plugin
- https://github.com/jenkinsci/docker-agent
- https://github.com/jenkinsci/docker-build-publish-plugin
- https://github.com/jenkinsci/docker-build-step-plugin
- https://github.com/jenkinsci/docker-ssh-agent
- https://github.com/jenkinsci/kubernetes-plugin
- https://github.com/jenkinsci/docker-slaves-plugin
- https://github.com/jenkinsci/docker-custom-build-environment-plugin
