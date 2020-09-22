# spring petclinic example

- Maven requires java as a pre-requisite
- petclinic uses Maven Wrapper `mvnw(.cmd)` to simplify access to `mvn`
- `spring-petclinic` example is attributable to the wonderful work done here: <https://github.com/spring-projects/spring-petclinic>

```shell
# create a fork of my repo if you want to push changes while following along
# or use mine without the ability to push changes
git clone <https://github.com/g0t4/jgsu-spring-petclinic>
cd jgsu-spring-petclinic

# TIP - I cannot emphasize enough, make sure the build works outside of Jenkins (and any other CI tool) before you try to wire it into Jenkins.
# In my younger days I struggled with build tools needlessly because I wouldn't break out of them to find out that the build tools were failing and the failure was obfuscated by my CI/CD tool (Jenkins, TC, etc).
# Use the following to take this example for a spin "manually" outside of Jenkins.

# Windows users, use ./mvnw.cmd
./mvnw --version # ensure maven works via wrapper
# fix any issues before proceeding (resources below for troubleshooting maven wrapper)

./mvnw # no args will give a build failure and prompt you for needed arguments, you can use this to see a failure in Jenkins as you're learning
./mvnw --help

# observe changes before/after, notably the `target` folder
./mvnw compile
./mvnw test
./mvnw package
./mvnw clean

# final command that does everything:
./mvnw clean package

```

## Resources

- [Maven](https://maven.apache.org/)
  - [Build Lifecycle](https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html)
  - [pom.xml](https://maven.apache.org/guides/introduction/introduction-to-the-pom.html)
  - [Standard Directory Layout](https://maven.apache.org/guides/introduction/introduction-to-the-standard-directory-layout.html)
    - *helpful for understanding inputs(`src`) and outputs (`target`) that need to be `linked` into `Jenkins`*
  - [Maven's Core Plugins](https://maven.apache.org/plugins/index.html#supported-by-the-maven-project)
    - Links to source code, for example the [maven-clean-plugin](https://github.com/apache/maven-clean-plugin/tree/master/src/main/java/org/apache/maven/plugins/clean)

- [Maven Wrapper](https://github.com/takari/maven-wrapper)
  - Maven v3.7.0 will include maven wrapper!
  - So long as the wrapper works, I recommend pretending it is the maven `mvn` command itself
