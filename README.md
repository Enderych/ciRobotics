CI-ROBOTICS
============================

# Guide

## Master computer
The following is only run **once** in your master comuter.

1. Fork this repo to your github account and then git clone to local.
1. Run `cd ciRobotics`
1. Run `. masterrun.sh` to init a swarm andd creat a gitlab servo.
1. Wait two minutes to start a gitlab server. Go to `localhost:7001` to check whether the gitlab is ready.
1. If it is ready, the page will ask you to set a password. Set any password you want. Then you will have a root accout with username `root` and password you have used.
1. Go to `Admin/runner/shared runner` to copy the shared runner token.
1. Paste the runner token in file `sharedrunnertoken.txt`
1. Run `. runnerReg.sh` to register a shared runner for the gitlab.
1. Run `. first.sh` to start a swarm service. Here, some info abot master computer will be pushed to github under your account for future use of worker computers.
1. RUN `sudo ./second.sh`. This step need a sudo privilege becasue it will add a domain name in your `/etc/hosts` and modify `/etc/docker/daemon.json` to use registry in an easy way(insecure).

## Worker computers
1. git clone **your repo** in local. Careful, not `yanjundream/ciRobotics`
2. Run `cd ciRobotics`
3. RUN `sudo ./second.sh`. This step need a sudo privilege becasue it will add a domain name in your `/etc/hosts` and modify `/etc/docker/daemon.json` to use registry in an easy way(insecure).

## Example use case
After setup the *Master computer* and *Worker computers* successfully, then it will be easy to use it in any of your projects. 
1. Go to your github project folder.
1. Run `git remote add *your_local_gitlab_project_address*`
1. Run `git remote set-url --add --push origin *your_local_gitlab_project_address*`
1. Run `git remote show origin` to check whether you have both push address.
1. Add `.gitlab-ci.yml` and `Dockerfile` and enjoy the continuous intergration of robotics software.
