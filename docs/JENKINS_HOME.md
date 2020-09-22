## What is JENKINS_HOME

- `JENKINS_HOME` is where Jenkins stores data on disk, such as:
  - system `config`, `plugins`, `fingerprints`
  - `workspaces` (temp directories for executing jobs aka builds)
  - `jobs/[JOB_NAME]` (each job has its own nested folder under jobs where job (aka project) config resides as well as its `build history`)
  - `build history` (jobs/[JOB_NAME]/builds), each `build` (aka `run`) has its own folder named after the `build number`
- `JENKINS_HOME` docs: <https://wiki.jenkins.io/display/jenkins/administering+jenkins> including backups/restores/job manipulation on disk...
- Location defaults to `~/.jenkins`
- Can set with env var OR system property, both named `JENKINS_HOME`

## When running in a Docker container:

The `jenkins/jenkins` Docker image has `JENKINS_HOME` set to `/var/jenkins_home`

### Bind Mounting JENKINS_HOME

- use volume short syntax: `./jenkins_home:/var/jenkins_home`
  - will create `./jenkins_home` if it doesn't exist on the `host`
  - path is relative to `docker-compose.yml` or `$PWD` for `docker container run`
- Docker docs for bind mounts: <https://docs.docker.com/storage/bind-mounts>
- Considerations
  - Bind mounts are easily `host` accessible granting you access with all the tools (CLI and GUI) installed on the host.
  - Can cause permission issues when dealing with host fs issues versus container... especially possible if using `Docker Desktop for Mac/Windows`
    - but not always going to be a problem, often works fine.
    - TIP: If you get random errors that seem disk related, check if removing the bind mount fixes the seemingly random issue.

### Named volume for JENKINS_HOME

- use volume short syntax: `jenkins_home:/var/jenkins_home`
  - tells docker to create or reuse a `named volume` called `jenkins_home`
- Volume docs: <https://docs.docker.com/storage/volumes>
  - volume drivers allow pluggable storage
  - by default it's a folder somewhere on the host
- Considerations
  - explicit name makes it easy to know what is what in `docker volume ls`
  - explicit name means it won't be cleaned up with `docker volume pr`
  - named volumes outlive (typically) the initial container they were attached to so naming grants an independent lifecycle versus the container using the volume

### Anonymous volume for JENKINS_HOME

- If you don't specify a volume mapping for `/var/jenkins_home` then an anonymous volume will be created because the `Dockerfile` for the official `jenkins/jenkins` image codifies this special directory so it is persisted.
- Considerations
  - anonymous volumes are intended to be disposable
  - anonymous volumes often are removed when the associated container is removed
