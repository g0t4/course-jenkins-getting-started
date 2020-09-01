# History

A bits of history to be aware of, especially terminology evolutions.

## Changed terms / term mapping

Jenkins is a large, open-source effort with a vast community supporting it, notably the ecosystem of plugins. As such, changes take time to propagate and that can be years. Effectively several terms are now aliased and so it is helpful to be aware of a mapping between previous and current terminology.

- `Jenkins` was first known as [`Hudson`](https://en.wikipedia.org/wiki/Hudson_(software))
  - `Hudson` was initially released in 2004 at Sun Microsystems
  - [Oracle acquired Sun in 2009/2010](https://en.wikipedia.org/wiki/Sun_acquisition_by_Oracle).
  - A dispute over trademarking the name `Hudson` led to the community renaming/forking the project to [`Jenkins` in Jan 2011](https://en.wikipedia.org/wiki/Hudson_(software)#Hudson%E2%80%93Jenkins_split).
  - Two forks emerged as Oracle also committed to maintaining `Hudson`
  - Politics aside `Jenkins` won the "popularity" contest early on as the community coalesced around the `Jenkins` project (fork).
  - `Hudson`'s last release was in 2016 [under the Eclipse Foundation.](https://en.wikipedia.org/wiki/Hudson_(software)#Move_to_Eclipse_Foundation)
- What is now the predominant platform of plugins referred to as `pipeline` was initially named `workflow`
- `master`/`slave` was the original terminology for distinguishing nodes.
  - Long ago `slave` was renamed to `agent`.
    - `slave` was deprecated as part of Jenkins 2.0
    - [Agent terminology cleanup](https://issues.jenkins.io/browse/JENKINS-42816) highlights the undertaking required to rename a prevalent term that permeates a decades old open-source ecosystem.
  - Recently (mid 2020) `controller` was selected to replace `master`.
    - This has yet to be reflected in the [glossary](https://www.jenkins.io/doc/book/glossary/) which is one of many reasons why I do not know if this renaming is a done deal.
  - Neither change is anywhere near complete so expect to see a mix of both for a while (years). I'll update this if changes are made, let me know if you hear anything definitive.
- `blacklist/whitelist` are being deprecated/discouraged and replacements suggested but not enforced (yet), ie allowlist/blocklist... that's my cursory understanding as of mid 2020.
- For more about terminology changes, [learn more here](https://groups.google.com/g/jenkinsci-dev/c/CLR55wMZwZ8?pli=1) and [here](https://docs.google.com/document/d/11Nr8QpqYgBiZjORplL_3Zkwys2qK1vEvK-NYyYa4rzg/edit#) and likley elsewhere including monitoring the [glossary](https://www.jenkins.io/doc/book/glossary/)
