# From Jobs to Pipelines

## Rooted in Builds

- App builds
  - Take inputs (source code)
  - Run a compiler or build tool that invokes one under the hood.
  - Capture outputs (logs, files)
  - and Report back (notifications).
- `builds` were one of the first prevalent tasks to automate.
  - Hence the prevalence of `build` terminology in just about every automation platform, not just Jenkins...
  - Even `TeamCity` has only recently distinguished [`build configurations types`](https://www.jetbrains.com/help/teamcity/build-configuration.html#Build+Configuration+Types):
    - `regular build configuration`
      - so, builds...
      - and everything else that's not a defined `build configuration type`.
    - [`Composite type of build configuration`](https://www.jetbrains.com/help/teamcity/composite-build-configuration.html)
    - [`Deployment type of build configuration`](https://www.jetbrains.com/help/teamcity/deployment-build-configuration.html)
- I am documenting this not to criticize anything, but so that you can disambiguate the explosion of often overlapping terms in any CI/CD tool, Jenkins included.
  - Don't get frustrated, **pick the term you like** and stick with it, **don't fret over the "proper" term in a given situation** just get your point across. There's no one right term in almost every situation 😃
- *Try this:* everywhere you look, even in current versions of Jenkins you will find relics of the fundamentals of building apps (notably the word `build`)
  - Console output / logs
  - Source code
  - Web UI (build steps, builds, build results)
  - Email notifications
  - Plugin names! (even suggested plugins and the setup wizard)
  - TODO - REVIEW - Even in `pipelines` relics of the prevalence of `builds` linger in the form of `steps` (aka `build steps`) and `publishers` (aka `post build actions`)
  - After two decades the `build` parlance lives on!
- `job` is a good generalization of `build` because it isn't specific in what it can accomplish.
  - `build` `jobs` were just the beginning!

## Myriad Jobs

Take a minute and think what all would be nice to have automated when it comes to the work you do. Here's some ideas from my early days of software development:
  
- `automated unit testing` - testing gives me confidence to run, not walk. Also, running tests on every check-in makes testing all the more worthwhile.
- `database migrations` - this blew my mind, the thought of methodically changing schema and/or modifying data to fit new purposes and doing so in a reproducible manner so that when you get to a `prod deploy` there are 🙏 no surprises.
  - That means no manual execution of hand-crafted SQL scripts (Sunday at 2am).
- `deployments` - what if the app was just deployed every time a check-in passed muster?
- `provisioning` - what about the infrastructure that runs the app? How does it get created? What if it just appeared! What if it was reproducible!
- `smoke testing`/`integration testing` - what about tests that require multiple components that may each be updating?
- `manual testing` - what if you had an automatically updated environment that people could run manual tests against? Or exploratory tests?
- `demo instances` - what if you white label your software and want to setup demos for prospective and/or seasoned customers?
  - What if you could parameterize a `job` to take a customer name and spit out a running instance of your app to demo, fully loaded with data!
- `upgrade testing` - what about when customers want to update, what can go wrong? Can you write tests to mitigate failures?
- `parallel testing` - what about slow tests? How can we speed them up? Some tests can (and should) be nuked but beyond that we need a mechanism to spread out the load and/or scale up capacity to handle the peak demand of 9to5 work.

## Reality is like a `workflow` or a `chain` of `jobs`

- The above `jobs` are all part of the process of getting from idea to working software.
- `workflows` - linking the `jobs` helps us model and automate a `workflow`, such as:
  - `build`
  - then `deploy to a test environment`
  - then `run integration tests`
    - when time consuming, run tests or test sets in parallel
  - then `deploy to a manual testing environment`
  - pause for humans to tinker with `manual and exploratory tests`
  - if all is well, `simulate a production deployment` including tests
  - if that passes, then `deploy to prod`
  - This is likely a simple workflow compared to reality, after all this workflow doesn't mention databases!
- `job chaining` or `build chaining` was doable with `upstream` and `downstream` `job` `linking` forming a `workflow` or `pipeline`
  - Someone checks in changes, a `build` job is triggered
  - The `build` succeeds so then you want to run the next job: `deploy to a test environment`
  - That means the `build` job is `upstream` to the `deploy to test environment` job which is `downstream` to the `build` job.
    - Think of a stick (compiled app) floating down a stream of water.

## Why not create a single job to rule them all

- That's viable but with the tooling in early versions of Jenkins it was prohibitive for a variety of reasons.
  - `jobs` just weren't created to model `pipelines` thus `linking` was necessary and unfortunately tedious!
    - **This is one of the reasons I loathed Jenkins v1! And it's the impetus behind the most fundamental change in v2!**
  - Compound this with having multiple apps needing similar `pipelines` and the work to set that up explodes!
- Back to the question of one job to rule them all, well ok but...  
  - Imagine you fail in the middle of a `pipeline`, can you retry just the part that failed? Is that safe?
    - Often with failures you just need to retry the `job` that failed and not re-run `upstream` jobs.
    - 😈 like when you're configuring a new `pipeline` and troubleshooting failures inside Jenkins without first checking them alone at the command line!
      - Woops, I forgot a semicolon in my prod deploy script... there goes 30 minutes of testing!
  - Say you lose internet for a second while `deploying to a test environment`, why would you want to compile and run unit tests again? That's silly, time consuming and potentially error prone.
- There's good reason to split up a `pipeline` into multiple linked `jobs` and `promote` `artifacts` between `jobs` as needed. A simple example is that you want to take the app you packaged up in your `build` job and deploy it in each `deploy` step.
  - Definitely you don't want to deploy an untested version of the app because someone committed a new change while you were testing a previous version. So you need traceability of artifacts.
  - You don't want to define, let alone compile your source in each `job`... just imagine the wasted time!
    - O(n) wasted where n is the number of jobs.
- Partitioning a pipeline is helpful to:
  - Visualize progress
  - When a failure happens you already know what subset (job/stage) failed.
  - You likely can re-run from the point of failure
    - If the problem is independent of your app, like a network or power outage.
    - Or, if it's a code bug you'll need to fix it and re-run the entire pipeline.
    - Or, only re-run part of the pipeline if a test had a bug in it but the app code was fine.
  - Controlling how the pipeline executes is another argument for splitting it up.
    - Sometimes you want automated promotion such that `downstream` jobs run automatically if `upstream` jobs succeeded.
    - Sometimes you want manual approval.
    - Sometimes you want a bit of both, to manually schedule an automated promotion (deployment).
- All of this combined with the inflexibility and tedium of the legacy `job` approach with `linking` is what gave rise to `pipelines` defined in `code` instead of a rigid `job config form`.
