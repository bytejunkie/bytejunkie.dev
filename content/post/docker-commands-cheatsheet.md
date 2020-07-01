---
title: "Docker Commands Cheatsheet"
date: 2020-05-26T20:43:14+01:00
draft: false
---

These are some of the more basic commands I will use when I'm working with the carpics container.

```
# search for an image
docker search alpine

# pull an image from a repo
docker image pull ubuntu:latest

# view local images
docker image ls

# build the docker file into an image
docker image build -t carpics:latest .

# run a container
docker container run -it ubuntu:latest /bin/bash
docker container run -it microsoft/powershell:nanoserver pwsh.exe

# stop and remove a container
docker container ps # to get the container id
docker stop <id>
docker rm <id>

#docker compose commands
#bring a compose app up and detach
docker-compose up -d
# stop
docker-compose stop
#stop and remove
docker-compose down

#docker stock commands
docker stack deploy <docker-stack.yml> <stackname>

# lists all stacks
docker stack ls

# info on a stack 
docker stack ps <stackname>

# remove a stack
docker stack rm
```