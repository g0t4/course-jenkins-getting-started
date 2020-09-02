# History

A bits of history to be aware of, especially terminology evolutions.

## Terms related to what you automate with Jenkins, that I think of as `functions`

- Jenkins is a large, `open-source` effort with a vast `community` supporting it, notably the `ecosystem` of `plugins`.
  - `Jenkins Core` is the foundation upon which plugins define the behavior of a given `Jenkins` `install`/`instance`/`environment`.
  - As such, changes take time (often years) to propagate. Especially true when changing terms. Several terms are de facto `aliased` and so it is helpful to be aware of the mapping between previous and current terminology. I'll provide that along with an explanation of prominent terms you should know.
- `mindset` - It's important to have a perspective with which you organize your understanding of any given subject. Here's my `mindset` to organize `Jenkins` and make it more intelligible. Your `mindset` may vary (YMMV 😉)
  - I find it helpful to contrast
    - `long running processes`
      - such as a GUI app like VSCode, or `Jenkins`!
    - versus `one-off`/`task`/`short lived processes`
      - such as a virus scan, disk defrag, or an app build with `maven` or `dotnet`
  - `tasks` must be triggered somehow
    - `manually` by a human (aka `long running process`)
    - `scheduled` to repeat with a tool like `cron`
    - `react` to some event
      - notably with software dev we often want to trigger `tasks` in relationship to changes being published to say a `git` repo
        - an `on push` or `on share` trigger, whatever lingo floats your 🚣
      - event detection varies
        - `poll` model - a `long running process` like Jenkins can `poll` for changes
          - `polling` is likely triggered on a `schedule` because `polling` for changes to detect an event is yet another `task`!
        - `push` model - an external `process` notifies Jenkins of changes and then a `task` in Jenkins will confirm (ie the `poll` task) and fetch changes to then trigger user-defined `tasks` to say `compile` an app.
  - I recommend a `function` mindset to grok the `tasks` you configure Jenkins to automate. So, user-defined `short lived processes` can be thought of as `functions`!
    - Somewhere exists a `function declaration` (aka `configuration` or `code`)
    - A function has `input(s)` (aka `parameter(s)`)
    - It `runs`/`executes` on the `inputs` (clone git repo, compile app, run tests, etc)
    - Concurrently `logs` progress, often via `STDOUT`/`STDERR`
    - Produces `outputs`/`artifacts` in the form of file(s)
      - Even `logs` can be thought of as `outputs`/`artifacts`... `STDOUT` is just a default file descriptor for writing output!
    - Select and archive `artifacts` for later retrieval
    - Ironically, most of what I said here about functions is just a template of a function declaration!
    - **TLDR: `Jenkins` is comprised of `long running processes` that trigger `executors` to run `functions`**
  - A big reason I like to think in terms of `functions` is because the actual terminology in Jenkins is murky at times.
    - That's because the typical use case of Jenkins (and similar tools) has evolved (roughly from building, to CI and now to CD).
    - And many other use cases are logical:
      - I could backup a database.
      - Or scrape data off of a website and store it for later processing.
      - Or perform cleanup on disk to save space, perhaps triggering this when free space runs low and/or on a schedule.
      - Calling these `builds` wouldn't make much sense! But, there are parts of Jenkins parlance that would refer to it as such, largely for historical reasons.
- `job`/`project` are generic to capture a wider array of possibilities.
  - And even [job is marked deprecated in the Jenkins glossary here](https://www.jenkins.io/doc/book/glossary/#job) while it is used all over the code, UI and docs!
- `pipelines` are a hugely popular feature in Jenkins v2 and have in many cases become another alias for `project`/`job` etc...
  - And of course before `pipeline` this feature set was known as `workflow` and you'll see that at times
- `items` are a generic term that encompasses `folders`, `projects` and `jobs`
- `folder` is an `item` to group related `items`
  - just like folders on a filesystem
- `VCS`/`git` - I assume you are familiar with version control tools and specifically `git` which is ubiquitous.
  - As opposed to folders of code without versioning like was popular back in the day 🙉!
  - If you want a challenge you could setup a Jenkins project to build from a network share!
- `build`/`build result` - the output that's captured for a given run of a `project`/`pipeline`/`job`/`function`/`task`

## Hudson and the origins of Jenkins

- `Jenkins` was first known as [`Hudson`](https://en.wikipedia.org/wiki/Hudson_(software))
  - `Hudson` was initially released in 2004 at Sun Microsystems
  - [Oracle acquired Sun in 2009/2010](https://en.wikipedia.org/wiki/Sun_acquisition_by_Oracle).
  - A dispute over trademarking the name `Hudson` led to the community renaming/forking the project to [`Jenkins` in Jan 2011](https://en.wikipedia.org/wiki/Hudson_(software)#Hudson%E2%80%93Jenkins_split).
  - Two forks emerged as Oracle also committed to maintaining `Hudson`
  - Politics aside `Jenkins` won the "popularity" contest early on as the community coalesced around the `Jenkins` project (fork).
  - `Hudson`'s last release was in 2016 [under the Eclipse Foundation.](https://en.wikipedia.org/wiki/Hudson_(software)#Move_to_Eclipse_Foundation)

## Architecture & changed/changing terms

- `node` - a long running process hosting either a Jenkins `agent` or `master`/`controller`
- `executor` - a `slot` that can run a single `project`, any `node` can have 0+ `executors`
  - in larger setups it is typical to not have `executors` on the `master` node to offload all build demand onto `agents` to avoid overwhelming the coordinating `master` node which has plenty of tasks to perform as you scale up demand.
- `master`/`slave` was the original terminology for distinguishing nodes.
  - Long ago `slave` was renamed to `agent`.
    - `slave` was deprecated as part of Jenkins 2.0
    - `agent` is popular in Jenkins alternatives like TeamCity and so it is natural to assume it is easier to onboard new users if terminology is familiar, and hence this change in v2 which was all about making it easier to get up and running with Jenkins quickly.
    - [Agent terminology cleanup](https://issues.jenkins.io/browse/JENKINS-42816) highlights the undertaking required to rename a prevalent term that permeates a decades old open-source ecosystem.
  - Recently (mid 2020) `controller` was selected to replace `master`.
    - This has yet to be reflected in the [glossary](https://www.jenkins.io/doc/book/glossary/) which is one of many reasons why I do not know if this renaming is a done deal.
  - Neither change is anywhere near complete so expect to see a mix of both for a while (years). I'll update this if changes are made, let me know if you hear anything definitive.
  - I personally refer to the `master/controller` as `Jenkins` and then if applicable `agent(s)`.
  - The `controller`:
    - Stores configuration
    - Hosts the web UI
    - Schedules/Coordinates/Distributes execution of `functions` (`pipelines`/`projects`/`jobs`) across `agents`
    - And interacts with agents to retrieve and store `output`/`results`/`artifacts`
- `blacklist/whitelist` are now discouraged and replacements suggested but not enforced (yet?), ie `allowlist/blocklist`
- For more about terminology changes
  - [learn more here](https://groups.google.com/g/jenkinsci-dev/c/CLR55wMZwZ8?pli=1)
  - and [here](https://docs.google.com/document/d/11Nr8QpqYgBiZjORplL_3Zkwys2qK1vEvK-NYyYa4rzg/edit#)
  - and likely elsewhere including monitoring the [glossary](https://www.jenkins.io/doc/book/glossary/).
- `JENKINS_HOME` - where Jenkins stores files (running builds/steps, or storing results and artifacts).
  - [Learn more here](https://wiki.jenkins.io/display/JENKINS/Administering+Jenkins)
- `workspace` - a temporary, disposable directory to house files for the work requested (git clone, compile, test, package, etc)
  - typically left in place between runs of a `project`
    - can be helpful to speed up builds when caching / partial compilation is present in build tools
    - can be painful if it makes builds hard to reproduce, or leads to flaky tests
    - can be cleaned up before/after a `project` runs depending on the `project` config, usually isn't cleaned up by default
  - Workspaces are default located in `$JENKINS_HOME/workspace/[JOB_NAME]`
    - the `[JOB_NAME]` in the jenkins wiki shows that `job` was and still is a common term.
    - anyways, each `job`(`project`) has its own workspace on a given node

## later

- Fingerprint
- Cloud
- Label
- Step (build steps, SUCCESSFUL/FAILED)
- Publisher (post-build actions/steps, STABLE/UNSTABLE)

## Pipeline terms

- `stage` is a grouping of `steps`
  - to visualize progress and results
  - For example,
    - a `"build" stage` might encompass compiling, unit testing and packaging an app
    - then a `"test deploy" stage` might encompass provisioning the app and running some higher level integration tests all of which ensures the deploy will work in prod and then leaves a test instance for humans to poke around.
    - then maybe a `"prod deploy" stage` which updates a production app.
    - sky is the limit
- `step` is a fine-grained task telling what actions to perform
  - I think of steps as a line of code
  - or shelling out to a CLI command (ie maven)

## Build status (aka Project Status technically)

- Each time you run a `job`/`project`/`pipeline`/etc Jenkins captures what it refers to as a build (result)
  - Look in `$JENKINS_HOME/jobs/[JOBNAME]/builds/` for a history of `BUILD_IDs` and the captured results (output)
- The irony is not lost that the result of running what is now a `Pipeline` or `Project` is often referred to as a `Build` or `Build status`!
- `Aborted` means the build was interrupted before completion (manually, timeout, otherwise).
- `Successful` means all build steps completed
  - `Failed` means a build step failed (ie a compiler error)
- `Stable` means no publishers reported a failure
  - ?Publishers (post-build steps) run after the build steps and thus can amend a `Successful` status to be more specific
    - a vestige (IMO) of the history of Jenkins.
    - an example might be a unit test parser that reads the result of running unit tests
    - `Publishers` are going to be configurable/nuanced in how they determine a failure (stable/`unstable`), so pay attention to the docs for a given `publisher`
- Personally I see a `job`/`project`/`function` as a set of steps and don't bother to distinguish `build` vs `post-build` or `publisher` steps... because why?
  - I wish we lived in a world where the `function` either aborted, failed or succeeded and really I just care if a problem exists, that the system helps me by telling me and makes it easy to dissect/troubleshoot.
