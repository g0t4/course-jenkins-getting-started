# Jenkins Getting Started

## 2nd Edition Examples **[CURRENT EDITION]**

- Course repositories:
  - [2nd Edition INDEX / COURSE OVERVIEW repo](https://github.com/g0t4/course-jenkins-getting-started). 
    - I recommend cloning this repo and/or clicking links provided! 
    - Each edition of the course has its own set of repos.
    - **AVOID GOOGLING** or **GITHUBOOGLING** (is that a word? :smiley:) and instead follow these links 
  - [spring-petclinic - example notes](docs/spring-petclinic.md)
    - repo: https://github.com/g0t4/jgsu-spring-petclinic
  - https://github.com/jenkins-getting-started/jgsu-spc-jenkinsfile
    - `spring-petclinic` `pipeline` ported to a `Jenkinsfile` in `git`
  - https://github.com/jenkins-getting-started
    - This is a GitHub org I setup with several repos for the last demo of the course, to be scanned by Jenkins

## 2nd Edition docs/notes

See the [docs](docs) folder for various additional notes I've left for you. Quite a bit of this is stuff not in the course that I wanted to share with you as you get started. Some of it is fodder for learning beyond the course. 

## FAQ

- **I am having an issue with building code in the `jenkins2-...` repository, how do I fix that**
  - If you are watching the updated / 2nd Edition course (most likely). Use the updated repos too ([see above](https://github.com/g0t4/course-jenkins-getting-started/blob/master/README.md#2nd-edition-examples-current-edition)).
  - If you want a challenge or are watching the 1st edition, try to adapt the 1st edition repos to work with the 2nd edition examples! A great learning opportunity!

## 1st Edition 

- The 2nd edition is an update to my original (1st edition) [`Getting Started with Jenkins 2`](https://www.pluralsight.com/courses/jenkins-2-getting-started) course.
  - You can follow this link to access the original course which is longer and has some content that wasn't included in the update given that we wanted to shrink the duration for placement into a jenkins learning path. And of course include relevant new features where applicable.
  - FYI the vast majority of content in the 1st edition is still relevant in the latest versions of Jenkins!
- In the 2nd edition update, the `2` is dropped from the course title even though I'm still covering the latest version of Jenkins which is still `2`.
  - Accordingly I have dropped the `2` from repos and instead use `jgsu` in many cases as a prefix.
  - `jgsu` = `jenkins getting started update`
  - `jenkins2` was the prefix of many first edition repos.
- [1st Edition Overview/Resources Gist (https://git.io/vKSVZ)](https://git.io/vKSVZ)
  - I share these mostly to avoid confusion with associated repos and examples that are and will continue to remain accessibly here on GitHub.
- This `Jenkinsfile` highlights a complex pipeline with multiple nodes involved and parallelism, for a challenge try to get this up and running on your own. Or at least read through it and grok what you think is needed to get it working.
