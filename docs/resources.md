# Resources



## Top level resources

- [jenkins.io](https://www.jenkins.io/)
- GitHub orgs 
  - [jenkinsci](https://github.com/jenkinsci)
  - [jenkins-infra](https://github.com/jenkins-infra/)

## jenkins-infra

Infrastructure projects
- [jenkins.io source](https://github.com/jenkins-infra/jenkins.io)
- [IEP - Infrastructure Enhancement Proposals](https://github.com/jenkins-infra/iep)
- [infra docs](https://github.com/jenkins-infra/documentation)
- 


## Resources Misc
             
- [Downloads](https://www.jenkins.io/download)
  - [Installing](https://www.jenkins.io/doc/book/installing/)
  - [JENKINS_HOME layout](https://wiki.jenkins.io/display/jenkins/administering+jenkins)
- Keeping up to date
  - [LTS Upgrade Guide](https://www.jenkins.io/doc/upgrade-guide/)
  - [LTS Changelog](https://www.jenkins.io/changelog-stable)
  - [Weekly Changelog](https://www.jenkins.io/changelog)
  - [Changelog Archive](https://www.jenkins.io/changelog-old)
  - [Roadmap](https://www.jenkins.io/projects/roadmap)
- [blog](https://www.jenkins.io/node/)
- Documentation
  - [Where to find documentation](https://www.jenkins.io/participate/document/)
  - NOTE: often you'll find parts of the jenkins.io docs out of date, most of the time it's not material but it happens and you should be aware that the docs are not always (as is the case in any project) the latest state of the codebase.
  - [User Guide / Handbook](https://www.jenkins.io/doc/)
    - [Glossary](https://www.jenkins.io/doc/book/glossary/)
  - [CloudBees](https://www.cloudbees.com)
    - [docs](https://docs.cloudbees.com/)
    - [Pipelines](https://docs.cloudbees.com/docs/admin-resources/latest/pipelines/)
      - [Checkpoints](https://docs.cloudbees.com/docs/admin-resources/latest/pipelines/administering-jenkins-pipeline#inserting-checkpoints)
    - [Plugins](https://docs.cloudbees.com/docs/admin-resources/latest/plugin-management/)
  - [Tutorials Overview](https://www.jenkins.io/doc/tutorials)
    - [Blog Post Tutorials (category)](https://www.jenkins.io/node/tags/tutorial/)
  - [Use-cases/Solutions Page](https://www.jenkins.io/solutions/)
    - find language/platform specific help
    - For example, [Docker](https://www.jenkins.io/solutions/docker/)
    - Or, [Java](https://www.jenkins.io/solutions/java/)
  - [Extending Jenkins](https://www.jenkins.io/doc/developer/)
- [Plugin Index](https://plugins.jenkins.io/)

## Scaling up

- [Distributed Builds](https://wiki.jenkins.io/display/JENKINS/Distributed+builds)
  - Controller/Agent model (formerly Master/Agent -> formerly Master/Slave)

### Labels

`Node` - (wes defined): any **`process`** running either the `Controller` or `Agent` Application.

`Labels` are a way to **identify** and/or **group nodes** based on characteristics that are pre-requisites for your `job`/`project` configuration... 

- [ci.jenkins.io labels](https://github.com/jenkins-infra/documentation/blob/master/ci.adoc)

Wes fodder for labels (think about what your automated tasks need and how to target nodes with those capabilities). It's kind of like if we all listed out the tasks we are good at and then along comes someone with a broken toilet... so we pull up all `plumbers` and hopefully someone is available and capable 
  (a label is no guarantee that it is accurate!)
Examples (a mix of Wes ideas and stuff I see in reality)
  - Hardware
    - RAM: `ram-2gb`, `ram-4gb`, `ram-8gb` etc
    - CPU: `slow`, `medium`, `fast` 
    - DISK: `ssd`, `hdd` or even ratings perhaps `max-read-speed-X` and `max-write-speed-Y`
  - Dev tools installed
    - Broad: `docker-cli`, `xcode`, `msbuild`, `jdk`, `maven`, `grade` `dotnet`
    - Granular: `jdk7`, `jdk8`, `jdk9`, `mvn3` or `mvn2`
  - Services
    - `iis`, `apache`, `nginx`, 
  - CPU architecture (`amd64`, `arm64`, `ppc64le`)
  - OS/Distro
    - Broad: `macos`, `linux`, `windows`
    - Broad: `debian`, `ubuntu`, `rhel`, `centos`
    - Granular: 
      - Linux distros 
        - `debian 9/stretch`, `8/jessie`
        - `ubuntu-(18.04.5|20.04.1|16.04.7)-lts`
          - (https://releases.ubuntu.com/)
      - Windows
        - `windows-server-(2004|1909|1903)`
        - `windows-server-(2019|2016|2012r2|2012|2008r2|2008`
        - `win10-(2004|1909|1809)`
        - [versions](https://en.wikipedia.org/wiki/List_of_Microsoft_Windows_versions)
      - macOS
        - `macos-10.(+15..12)`
        - `osx-10.(11..8)`
        - `macosx-10.(7...0)`
        - [versions w/ codenames](https://en.wikipedia.org/wiki/MacOS#Software_compatibility)
  - Browser 
    - `internet-explorer`, `chrome`, `firefox`, `edge`, `chrome-canary`
- Consider deferring combined labels to be a `"querytime"` feature not a `"labeltime"` feature
  - Instead of `ubuntu-20.04.1-lts` we might have:
    - `ubuntu` + `20.04.1` + `lts`
    - So I could target nodes with just `ubuntu` 
    - Or, I could say `ubuntu` + `lts` 
    - Or, `windows` + `server` + `2016`
  - Why? 
    - Avoid redundancy
    - Fewer labels, less time labeling.  
    - Explosion of combinations can be confusing to find what you need
    - Many labels will go unused
    - Many have zero relevance to the targeting you need
- Consider deferring the labeling process until needed unless it's broad and not a substantial cost. You could literally manually add labels to a small cluster if you need to query a subset of agents that you don't have labels to target.
- Consider dynamic labeling - when the jenkins "node" process runs it can sniff out (aka fingerprint) the environment to set appropriate labels for itself.  





## Pipeline resources

- [Pipeline Syntax Reference](https://www.jenkins.io/doc/book/pipeline/syntax/)
- [Pipeline Step Reference](https://www.jenkins.io/doc/pipeline/steps)
- [Plugin Compatibility with Pipeline](https://github.com/jenkinsci/pipeline-plugin/blob/master/COMPATIBILITY.md)

- Authoring `pipeline` scripts:
- [`Classic UI`](https://www.jenkins.io/doc/book/pipeline/getting-started/#through-the-classic-ui)
- [`In SCM`](https://www.jenkins.io/doc/book/pipeline/getting-started/#defining-a-pipeline-in-scm)
  - [`Jenkinsfile`](https://www.jenkins.io/doc/book/pipeline/jenkinsfile/)
  - [CloudBees `Jenkinsfile` docs](https://docs.cloudbees.com/docs/admin-resources/latest/automating-with-jenkinsfile/creating-jenkinsfile)
- [`BlueOcean`](https://www.jenkins.io/doc/book/pipeline/getting-started/#through-blue-ocean)
  - [`BlueOcean` docs](jenkins.io/doc/book/blueocean/)
  - Official docs list this as separate category but it's really just via SCM + BlueOcean UI generating pipelines
    - Arguably `BlueOcean` was yet another step toward the Freestyle project type... BUT, in terms of a simplified UI for pipelines... interesting to watch popularity drift back and forth as people have needs and are compelled to travel in differnet directions to solve those needs.
  - BlueOcean can generate/scaffold and commit Jenkinsfiles
  - Major dev of BlueOcean has stalled. From what I've read, as of late (2020), the goal is to use BlueOcean "lessons learned" to redesign the Classic UI (in time drastically).

## Groovy resources

- Pipelines are groovy scripts (close enough), so any groovy resources you have will be helpful.
- :+1: Knowledge of groovy
- Psychological Soap Box about `code` vs `config` vs `convention`   
  - AND instances of types of code (`groovy` vs `java`)
    or config formats (`xml` vs `json` vs `yml`) 
  - IMHO `groovy` is somewhat easy to read and thus it is learnable with less investment than say `shell scripting` 😉
  - I don't understand the supposition that people don't like code / can't code / don't want to use code... but somehow DSLs/configuration & convention (even more so) are superior in terms of grok-ability / preferable versus code... no, code/config/convention are all heads of the same coin.
    - **(hint: means not ends)** 
    - > tools in a toolbelt, carry all of them not just one
  - > We like what we are familiar with (and we tend to become more familiar with what we like and avoid things that are difficult because even if at one time they were familiar they grow distant out of frustration and thus lack of preference). It's self-fulfilling.

## Pipeline Syntax Live Docs/References

- These are docs that are built-in to a Jenkins instance and are often dynamic according to the plugins installed. Like adding the [`pipeline-as-yaml`](https://plugins.jenkins.io/pipeline-as-yaml/) plugin adds `Pipeline As YAML Converter` tool under `Pipeline Syntax`

- [Snippet Generator](https://www.jenkins.io/doc/book/pipeline/getting-started/#snippet-generator)

  - <http://localhost:8080/pipeline-syntax/>
  - Form based generation of steps for either a `scripted` or a `declarative` pipeline

- [Declarative Directive Generator](https://www.jenkins.io/doc/book/pipeline/getting-started/#directive-generator)

  - <http://localhost:8080/directive-generator>
  - Form based generation of nested directives (ie `when`)
    - NOT steps

- [Global Variable Reference](https://www.jenkins.io/doc/book/pipeline/getting-started/#global-variable-reference)

  - <http://localhost:8080/pipeline-syntax/globals>
  - `pipeline` declarative "entrypoint" is a global!

- [Pipeline As YAML Converter](http://jenkins:18080/job/vcs-spc/payConverter/)

  - Great example of adding a plugin (yaml pipelines) and seeing new docs light up under the [`Pipeline Syntax`](http://jenkins:18080/pipeline-syntax/) section

- [Pipeline examples](https://www.jenkins.io/doc/pipeline/examples/)
  - Sourced from [jenkinsci/pipeline-examples](https://github.com/jenkinsci/pipeline-examples)

## JCasC - Configuration-as-code

- Like pipelines-as-code did for freestyle jobs, configuration-as-code does for configuring the Jenkins `controller`
  - Historically, we've had `post-init groovy scripts` to modify the configuration of instances.
    - [Groovy Hook Scripts](https://www.jenkins.io/doc/book/managing/groovy-hook-scripts/)
- [README.md docs](https://github.com/jenkinsci/configuration-as-code-plugin)
- 

## IDE/CLI pipeline productivity tools

Assortment of tools to use on Jenkinsfile/pipelines outside of Jenkins:

- https://www.jenkins.io/doc/book/pipeline/development/
- jenkinsfile-runner (JFR)
  - v1.0 ~Dec 2020
  - Allows you to test Jenkinsfile locally without a hassle all via an official `jenkins/jenkinsfile-runner` image!

## Governance / Ecosystem / Community

- [Project Structure and Governance](https://www.jenkins.io/project)
- [JEPs - Jenkins Enhancement Proposals](https://github.com/jenkinsci/jep/)
  - Design of major new functionality that may or may not see the light of day.
- [Sub-projects](https://www.jenkins.io/projects/)
- [JCasC](https://www.jenkins.io/projects/jcasc/)
- [Jenkins X](https://jenkins-x.io/) - opinionated Jenkins mindset (not necessarily components of Jenkins) meets k8s as the clustering tech for everything from dev to prod.
- [Blue Ocean](https://www.jenkins.io/projects/blueocean/)
- [Evergreen/Essentials](https://www.jenkins.io/projects/evergreen/)
  - IIUC this has stalled too (services were never migrated earlier in 2020 to new prod cluster)
- [Infrastructure](https://www.jenkins.io/projects/infrastructure/)
  - [JIRA](https://issues.jenkins-ci.org)
    - by component, ie [Core](https://issues.jenkins-ci.org/browse/WEBSITE-760?jql=component%20%3D%20core)
  - [https://ci.jenkins.io](https://ci.jenkins.io)
    - Fun way to poke around and see some practical applications of Jenkins
    - Jenkins dogfooding itself!
- [Contributing / participating](https://www.jenkins.io/participate)
  - [Meetups](https://www.jenkins.io/projects/jam)

## TODOs to distill links into:

- https://github.com/jenkins-infra/documentation/blob/master/ci.adoc
- repos https://github.com/jenkins-infra
- other GH repos 
- https://www.jenkins.io/participate/document/
- https://www.jenkins.io/doc/book/pipeline/jenkinsfile/
- https://docs.cloudbees.com/docs/admin-resources/latest/automating-with-jenkinsfile/creating-jenkinsfile
- https://www.jenkins.io/doc/book/pipeline/getting-started/#directive-generator
- https://github.com/jenkinsci/pipeline-model-definition-plugin/wiki/Getting-Started
- https://www.jenkins.io/doc/book/blueocean/dashboard/