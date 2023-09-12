---
layout: post
title: Docker - Pandas
categories: study
sitemap: false
hide_last_modified: true
published: true

---

## [Docker] Docker and Kubernetes: The Practice Guide

## Docker

- is a tool for creating and managing containers
- supports for containers is built into modern operating systems
- simplifies the creation and management of such containers

### Container

- a package of code and dependencies to run that code, same container always yields the exact same application and execution behaviour
- why? different development & production environments
- why? different development environments within a team
- why? clashing tools/versions between different projects

### Container vs. Virtual Machine

- VM Pro
    - Separated environments
    - Environment-specific configurations are possible
    - Environment configurations can be shared and reproduced reliably
- VM Con
    - Redundant duplication, waste of space
    - Performance can be slow, boot times can be long
    - Reproducing on another computer/server is possible but may still be tricky
- Docker Container
    - Low impact on OS, very fast, minimal disk space usage
    - Sharing, re-building and distribution is easy
    - Encapsulate apps/environments instead of ‘whole machines’
- VM
    - Bigger impact on OS, slower, higher disk space usage
    - Sharing, re-building and distribution can be challenging
    - Encapsulate ‘whole machines’ instead of just apps/environments

### Docker set up

- Docker Engine
- Docker Desktop (including Daemon & CLI)
- Docker Hub
- Docker Compose

### Docker commands

- docker ps (showing all running containers)
- docker ps -a (showing all stopped and running containers)
- docker stop [NAMES]
- docker start [NAMES]
- docker rm [NAMES]
- docker rmi [ID]
- docker build .
- docker run -p [local port]:[internal container port] [ID]  → container created
- docker run -p [local port]:[internal container port] -d [ID] (detach mode)
- docker run node (download and run image)
- docker run -it [NAMES] (node interactive mode)
- docker logs [NAMES]
- docker cp [source] [dest-name]:[folder] (i.e. docker cp dummy/. aaa_bbb:/test)

### Dockerfile

- FROM [baseImage] → custom image based on the default node image with our own instructions
- WORKDIR [workdir]
- COPY [source - local] [dest - image file system]
- RUN [command i.e. npm install]
- EXPOSE [port]
- CMD [executable]→ start container start inside the image, should be last line

### Images & Containers

- containers: the running ‘unit of software’
- images: template/blueprints for containers, contains code, required tools, runtimes
- multiple containers can be based on the same image
- when we need an image → use an existing, pre-built image via Docker Hub, or create your own custom image based on another image by writing your own Dockerfile
- whenever one layer changed, all layers after that will rebuild.