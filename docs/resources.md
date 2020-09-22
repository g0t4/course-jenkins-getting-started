# Resources

- [Jenkins Project Site](https://www.jenkins.io/)
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

## Pipeline resources

- [Docker + Pipeline](https://www.jenkins.io/doc/book/pipeline/docker)

  - These two tools together are a formidable force for simplicity and yet flexibility in all sorts of complicated CI/CD pipeline scenarios.

- [Pipeline Syntax Reference](https://www.jenkins.io/doc/book/pipeline/syntax/)
- [Pipeline Step Reference](https://www.jenkins.io/doc/pipeline/steps)

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
  - Historically, we've had post-init groovy scripts to modify the configuration of instances.

## Plugin Manager 2.0

- <https://github.com/jenkinsci/plugin-installation-manager-tool>

## jenkinsfile-runner (JFR)

- v1.0 ~Dec 2020
-

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
  - [Jenkins 4 Jenkins!!](https://ci.jenkins.io/)
    - Fun way to poke around and see some practical applications of Jenkins
    - Jenkins dogfooding itself!
- [Contributing / participating](https://www.jenkins.io/participate)
  - [Meetups](https://www.jenkins.io/projects/jam)
