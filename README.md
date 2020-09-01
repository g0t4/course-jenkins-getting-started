# Jenkins Getting Started

This is an update to my original [`Getting Started with Jenkins 2`](https://www.pluralsight.com/courses/jenkins-2-getting-started) course.

FYI: The `2` is dropped from the title even though I'm still covering the latest version of Jenkins 2.
- This update also exists to trim some of the content for placement in a learning path. If you also want access to the [full 1st Edition course which is still largely relevant use this direct link](https://www.pluralsight.com/courses/jenkins-2-getting-started).

## Example repositories

These repos house examples for following along:
- [spring-petclinic](./docs/spring-petclinic.md)
- ... MORE COMING SOON ...

## 1st Edition resources

- Don't be confused by resources from the 1st Edition of my `Getting Started with Jenkins 2` course
- [1st Edition Overview (Gist)](https://git.io/vKSVZ)

## JCasC - Configuration as Code

Watch this area! And the ecosystem of related changes (see my ramblings here, I probably won't have time to fit much, if any, of this into the course and I wanted to share it with you).

- [Jenkins Configuration as Code `JCasC`](https://www.jenkins.io/projects/jcasc/)
  - [source](https://github.com/jenkinsci/configuration-as-code-plugin/blob/master/README.md)
- A primary focus of v2 was to reduce barriers to entry
  - to go from not knowing anything about jenkins to using it as fast as possible
  - or to standup new instances quickly even for experts
  - safe by default
  - hence, steamlined setup wizard (suggested plugins, create first account, URL, go!)
  - hence, pipelines/`Jenkinsfile`
- Setup can be further streamlined...
  - I know because a while back a I created a [bootable zero-config docker image](https://hub.docker.com/r/weshigbee/jenkins-bootstrapped) for another course so I didn't have to constantly wait for plugins to install and poke through the setup wizard and so I could avoid the specifics of Jenkins in that course as my courses tend to run long (I like depth! and I bet you do too if you're reading my thoughts here) enough as it is and I didn't want the overhead of demonstrating configuring, let alone explaining, jenkins. I wanted ready to go instances for myself and viewers.
  - Think Configuration Management with
    - reasonable defaults
    - jenkins config checked into a `git` repo!
    - just like `pipeline` (`Jenkinsfile`) did for jobs
    - yaml, yaml, yaml (instead of XML) - yaml is all the rage these days which doesn't inherently make it better
    - desire to eliminate/reduce need for groovy init scripts (IMO nothing is inherently wrong with scripting and that is why it...)
  - ...warms my heart to see JCasC get its own groovy plugin for groovy scripting!
    - <https://github.com/jenkinsci/configuration-as-code-groovy-plugin>
    - Perhaps one can say the goal is to simplify the scripting!
  - Config -> Code -> Config ... that's inevitable in all of software dev (back and forth)
    - System config:
      - Jenkins has [xml config](https://wiki.jenkins.io/display/jenkins/administering+jenkins) + [groovy init scripts](https://wiki.jenkins.io/display/JENKINS/Post-initialization+script)
        - [Configuring Jenkins upon start up](https://wiki.jenkins.io/display/JENKINS/Configuring+Jenkins+upon+start+up)
        - [Groovy Hook Scripts](https://www.jenkins.io/doc/book/managing/groovy-hook-scripts/)
      - JCasC brings yaml config + groovy scripts
    - Somewhat like jobs:
      - Freestyle projects/jobs (xml config)
      - Then (scripted) pipelines (code)
      - Then (declarative) pipelines (config-ish)
      - Now [yaml pipelines (config)](https://plugins.jenkins.io/pipeline-as-yaml/)
    - **IMHO a mix of both is best**
      - `config` (opinionated aka magic aka does much with a little bit of config that is intuitive)
      - `code` (flexibility)
      - I'm happy to see active exploration into making things better as long as its practical (eventually is fine ::smiley:: ).

## History

- `master`/`slave` was the original terminology for jenkins nodes.
  - Years ago `slave` was renamed to `agent`.
  - Recently `controller` was selected to replace `master`.
  - Neither change is anywhere near complete so expect to see a mix of both. And I'm not certain if the `controller` selection is yet a done deal but it may be. I'll update this if changes are made, let me know if you see any news before I get to it.
  - `blacklist/whitelist` are being deprecated/discouraged and replacements suggested but not enforced (yet), ie allowlist/blocklist
  - [Learn more here](https://groups.google.com/g/jenkinsci-dev/c/CLR55wMZwZ8?pli=1) and [here](https://docs.google.com/document/d/11Nr8QpqYgBiZjORplL_3Zkwys2qK1vEvK-NYyYa4rzg/edit#) and likley elsewhere including monitoring the [glossary](https://www.jenkins.io/doc/book/glossary/)
