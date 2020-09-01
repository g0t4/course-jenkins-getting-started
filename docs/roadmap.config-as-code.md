# Roadmap - Configuration as Code (JCasC)

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
