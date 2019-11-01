# Development Pipeline

Every project has to have an automated pipeline. It starts when we make a Pull-Request and ends if the tests of our projects failed or the when the it fully deployed to our Production env and everything works just fine.

Its important to remember this pipeline is going to be our only way to ensure our product quality. Neglecting this pipeline will directly effect our production env quality.

Automate everything needed for the Quality Assurance of the app. A Manual step which is not automated and not included in this pipeline is sentenced to die sooner or later, it's just not relevant any more to the modern development circle rhythm.

This is a summary of how a pipeline should look like:

- Git
- Merge/Pull Request
- Static Code Analysis
- Building and Storing an Artifact
- Deploy to QA, a prod-like environment
- Run runtime Tests (E2E, Integrations, Stress...)
- Deploy to Production
- Run Tests on production
- Rollback if needed

## Git

- Master branch
- No Dev branch
- Feature branches
  - will be deleted when Feature is done
- Push directly to master is not allowed, only with Pull-Request(GitHub, Bitbucket)/Merge-Request(Gitlab)
  - Before a merge request, make sure you have rebased(not merge) you changed on top of the master branch.
  - Before a merge request, combine all of your commits to one commit.
  - Keep them as small as possible. Large MergeRequest is a bad sign of a large task not splitter well to small independent parts.
    - Commit often
- Stop using GitBash. It doesn't make you more manly. GitKraken/SourceTree will save you tons of time.
- Write good commit messages
  - for example "HotFix" - will be use for fast deploy
  - Generate a changelog from your git commit messages, it will make you and your team write understandable ones.
- Make sure you .gitignore is covering all unnecessary files
  - There are good .gitignore example for each project type.

## CI tool

The CI tool will automate your whole process. The pipeline begins when you create a new Pull-Request on the git server in which it listens to.

The pipeline takes the whole repo code, with the new added code, and begin the pipeline.

- Famous CI tools: Jenkins, CircleCI, TravisCI, GitHub CI an so on..
- Most of the CI tools are working in a master-slave architecture
  - The slave agent will run all your pipeline commands
  - Make sure to install all needed dependencies and the specific version you need (NodeJs, .Net Core SDK, Git client..)
  - Most CI tools will let you run the agent on a container
    - Prefer this option, as with containers you easily build your agent container based on read-made containers
    - You can even use a different containers for different steps.

## Static Code Analysis

The first stage of the pipeline is to run all analysis we want on our code, which doesn't require to execute the code

- Linter
  - Eslint (Tslint is dead)
  - C# Reshaper
  - Sonar linter
- Unit Tests
  - NUnit/XUnit/MSTests
  - Jasmine/Mocha/Jest
- Test Coverage
- Code Smells of bugs and lang-related conventions
  - Sonar
- Security vulnerabilities

- Static Analysis must be super fast
- You can ran it per each service in repo, out all together, it doesn't really matters

## Building the Artifact

Each change in the code will have it's own artifact, which is the release-ready compiled code.
The artifact will be saved in some repository, there, it will be managed like all other libraries, by it's id and increasing versions.

- Compile Code in release mode
  - Language related optimization
    - Webpack on Production mode (Link to setting Webpack to production)
      - Minification
      - Uglification
      - Chunks
      - Compression
      - Source Maps
    - .Net on 'Release' mode
      - Sign dll (Not must, only if releasing the dll tor public usage)
    - Configuration file
      - Artifacts are logical-configuration free. The are not related to any of your logical environment.
        - Configuration environment will be selected on runtime, by reading it from your Hosting Environment Variables
      - Otherwise, you will have to build an artifact for each logical environment which is a waste of time and storage
      - To Conclude: Compilation step has nothing to do with configuration files
  - Optimize Artifact
    - npm pune will remove all dev dependencies
    - Delete un wanted files and directories
- Build a Docker container: (Link to docker specific BP)
  - Make use of MultiStaging technic to speed up your container performance and shrink it's size
- Versioning:
  - [Read Here](Versioning.md)
- Publish and Store the Artifact to an organized Repo.
  - Repo just like Npm, Nuget, Pypy, Dockerhub, or just a custom Repo of your own.
  - Artifactory is a nice tool.
  - If you have no Repo server, save it to File System, by it's version.
  - Tag the artifact as 'unstable', as it haven't fully tested yet, so it is not ready to run on production environment.
- In case there are many services, build can be done concurrently for each step.

## Deployment

This section will describe the best practices to how deploying an release-ready Artifact to our Hosting environment, no matter of the logical environment(Prod, QA, Demo...)

- Zero Downtime
  - Blue Green Algorithms
    - Just before each service you shut down, set the LoadBalancer referencing this service to a drill down mode - which will stop receiving new requests and wait until al existing requests are finished.
  - Make sure your new code is [backward compatible](../ApiServices/ZeroDownTime-BackwardCompatibility.md)
- Deploy all services exists in the triggered git repo.
  - You must asking why? We only changed code in one service, not in all of them.. It will be waste of time to deploy..
    - What are you afraid of in deploying all of the services?
      - Time? - Run all deployment concurrently
      - Failure? - In good automation script and tools, there is not reason why a deployment will fail. Failure is good, so you can learn for other times, when you will really need that specific service to be deployed.
      - Down Time? - Please look above at "Zero Down-Time" section.

### Deploying to 'QA'

- Deploy to QA environment
- Make sure this environment is [Prod-Like]() LINK
- Set the Environment Variable of the hosting OS to the right logical environment 'QA', so 'QA' configuration will be loaded at startup
- Number of QA environments
  - Since we commit often, and trigger our pipeline a lot. In a project with many developers, this pipeline can become a bottleneck.
  - We can solve it by creating multiple 'QA' environments
    - VMs - it is hard to manage and can be very costly to have multiple QA prod-like environments
    - K&S - Easy to create and destroy environments, thus, using only the resources when needed.
      - One environment per commit - Crazy

## Runtime Testing

After the whole environment is up, it's time to run all the more important tests.

- Environment warmup - give it some time, K&S might still replacing old environment and tests could fail because of slow startup.
- Kind of Tests to run:
  - Integration Tests
  - GUI (E2E) Tests
  - Visualization Tests
  - Stress and Performance Tests
  - Google Lighthouse
- Hard Core Mode - After all tests successfully run - automatically check your logs and fail the pipeline if a Critical Errors has logged during the Runtime Tests.
- These kind of tests tend to have a long execution time
  - In case execution time of the tests becomes a development bottleneck, there are some hacks you can do:
  - "Sanity Check" vs "Full Tests"
    - When seeking a quick feedback to our new code, it's not super important to run all kind of tests.
    - Choose as "Sanity" only what really important for you. For example: 20% of the GUI tests, 50% of API tests, no Load and Performance..
    - Use git commit message to decide whether to run Sanity or Full tests.
    - Don't push it too much, it's a quick downhill(ניסוח) to stop running the Full set of tests.
  - You can try run all of the tests simultaneously, although it will be super hard to track issues, which is already not an easy task.

## Deploying to Production

In case all tests has passed successfully, which is a miracle, especially when talking about flaky E2E tests which are the horror of the modern development(LINK to E2E tests)

- Automatically deploy to production after tests successfully passed.
  - Are you afraid? Why? It just mean you did a bad job creating a Quality Pipeline Gate.

## Run Tests on Production

- Run only sanity checks. We just need a good quality quick feedback if everything is alright after the deployment.
- Make sure you tests can handle production environment and are not going to destroy it or corrupt the data.
  - More details in E2E tests (LINK)
- If tests pass successfully
  - Mark the Artifacts as Stable.
  - Automatically Merge code into master
  - Make a Git tag to this commit with the name of the new version
- Run this step as a routine on your production on idle times. [More Details](Routines.md)

## Rollback if needed

In case Sanity tests has failed on Production environment it means things went wrong and we must rollback to the last previous version

## [Infrastructure as a Code](https://www.thorntech.com/2018/01/infrastructureascodebenefits/)

Put everything you can as a CODE in your REPO:

- Source Code
- Pipeline code
  - Building Scripts
  - Testing Scripts
  - Deployment scripts
- Docker & K&S
  - OS
  - Third Party installations (NodeJs,.Net Runtime,Python ..)
  - LoadBalancer
  - ApiGateway

Benefits of IaaC:

- Not putting you infrastructure as a Code mean you set them manually - which is is dark and full of terrors
- Easy and Fast to modify
- Part of your ONE Artifact
- Easy to upgrade OS layers (Upgrade OS version, Upgrade os installations)
