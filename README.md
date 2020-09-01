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

## History

- `master`/`slave` was the original terminology for jenkins nodes.
  - Years ago `slave` was renamed to `agent`.
  - Recently `controller` was selected to replace `master`.
  - Neither change is anywhere near complete so expect to see a mix of both. And I'm not certain if the `controller` selection is yet a done deal but it may be. I'll update this if changes are made, let me know if you see any news before I get to it.
  - `blacklist/whitelist` are being deprecated/discouraged and replacements suggested but not enforced (yet), ie allowlist/blocklist
  - [Learn more here](https://groups.google.com/g/jenkinsci-dev/c/CLR55wMZwZ8?pli=1) and [here](https://docs.google.com/document/d/11Nr8QpqYgBiZjORplL_3Zkwys2qK1vEvK-NYyYa4rzg/edit#) and likley elsewhere including monitoring the [glossary](https://www.jenkins.io/doc/book/glossary/)
