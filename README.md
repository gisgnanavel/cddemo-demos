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


## Note
if you use docker on OSX/Windows relying on boot2docker, the docker job will fail (shell script step hang). This is due to workspace mount, which reference /var/jenkins_home from the docker container hosting jenkins, which itself is a bind mount from your local directory. But subsequent attempt to bind mount /var/jenkins_home do run from dockerhost, and as such is missing this folder. As a workaround, ssh the docker machine and run: `sudo ln -s /Users/xxx/path-to-demo-directory/jenkins-home/ /var/jenkins_home`.
I'm looking for a fix in docker-workflow-plugin using `--volumes-from` ...