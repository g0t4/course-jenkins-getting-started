# Dockers

Nothing but net to master both containerization and Jenkins and merge the two where each exhibits a strength.
- For example, a `Dockerfile` in many ways is very much like a `Jenkinsfile` as each can execute a build (test too, sytle checks, etc) and produce artifacts worthy of keeping including the console output when they run. 
  - If you're familiar with Docker's multi-stage image builds, you'll know how to easily incorporate a variety of "upstream" and "official" tool images like for `maven` or `dotnet` and string them together to build a pipeline within a `Dockerfile`.... anyways I think contemplating the similarities and differences between `Dockerfile` and `Jenkinsfile` is a worthwile exploration. 

## Docker + maven example
https://github.com/jenkinsci/pipeline-examples/blob/master/declarative-examples/jenkinsfile-examples/mavenDocker.groovy