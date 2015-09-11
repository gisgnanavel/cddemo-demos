# (Docker, Jenkins) -> { Orchestrating Continuous Delivery }

"Continuous Delivery" is a major Buzz word, as "Docker" is, but in most blog I've read so far only minimalist trivial pipelines have been considered : compile, test, push docker image, that's it. Jenkins definitively is more than Continuous Integration, and with recently introduced workflow plugin we can fully automate in plain DSL a complex pipeline. Integration with Docker gives it even more power. During this session, I'll build such a pipeline from scratch to demonstrate workflow DSL usage and flexibility, as well as Docker support to run an actual Continuous Delivery process.

## step1 : "tinkener" 
show how we used to setup CD with a set of jobs and various plugins to chain them together
- hard to setup, maitain, diagnose
- jobs get poluted by plumbing plugins

## step2 : "craftsman" introduce orchestration modelization with build-flow
demonstrate use of a DSL to define the CD process as a set of simpler steps (actually, jobs)
- simple, robust
- no single log
- pipeline config is divided in various places 
- 'step' are job, but for most of them just include some basic build steps

## step 3 : "professional" introduce workflow
- simple DSL, can learn using snippet generator, better doc to come
- easy to share and review
- Jenkinsfile !

## step 3 : "future" introduce docker workflow
- stop relying on jenkins to define the build environment
- everything is set in SCM. As images IDs or `Dockerfile`s


