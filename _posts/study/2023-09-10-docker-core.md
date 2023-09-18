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

### Managing Data

- Data
    - Application(Code+Environment) : Read-only, hence stored in Images
        → written and provided by developer
        → added to image and container in build phase
        → fixed: cannot be changed once image is built
    - Temporary App Data (i.e. user input) : Read + write temporary, hence stored in Containers
        → fetched/produced in running container
        → stored in memory or temporary files
        → dynamic and changing, but cleared regularly
    - Permanent App Data (i.e. user accounts) : Read + write, permanent, stored with Containers & Volumes
        → fetched/produced in running container
        → stored in files or a database
        → must not be lost if container stop
- Volumes
    - folders on your host machine hard drive which are mounted/mapped into containers
    - persist if a container shuts down. if a container (re)starts and mounts a volume, any data inside of that volume is available in the container
    - A container can write data into a volume and read data from it
    - Anonymous Volumes → managed by docker, “docker volume”, can be used to prioritise container-internal paths higher than external paths
        - docker run -v /app/data …
    - Named Volumes → managed by docker, great for data which should be persistent but you don’t need to edit directly
        - docker run -v data:/app/data …
    - Bind Mounts → managed by developer, you define a folder path on your host machine. great for persistent, editable (by developer) data
        - docker run -v /path/to/code:/app/code …
    - Docker supports build-time ARG and runtime ENV variables
    - ARGuments
        - available inside of Dockerfile, NOT accessible in CMD or any application code
        - set on image build (docker build) via - - build-arg
    - ENVironment
        - available inside of Dockerfile and in application code
        - set via ENV in Dockerfile or via - - env on docker run        

### Networking

- Container to WWW communication
    - by default, container can reach out to the www via ‘docker run’
- Container to Local Host Machine communication
    - use “host.docker.internal” as address
- Container to Container communication
    - requires a container network + use container name as address
    - docker, put all containers in one network with below command
    - docker run - - network my_networks …
    - then all containers can communicate with each other and IPs are automatically resolved

### Docker-Compose

- automating multi-container setups
- tool that allows you to replace ‘docker build’ and ‘docker run’ commands with one configuration file and then a set of orchestration commands build/start/stop all containers
- what docker compose is not
    - not replace Dockerfile
    - not replace images or containers
    - not suited for managing multiple containers on different hosts
- Writing Docker Compose Files
    - Services (Containers) → published ports, environment variables, volumes, networks

### Utility Containers

- only has certain environment in it.
- ‘docker run mynpm init’
- executes/appends custom command

### Deploying Docker Container

- deployment to production
    - bind mounts should not be used in production
    - containerised apps might need a build step (i.e. React apps)
    - multi-container projects might need to be split across multiple hosts/remove machines
    - trade-offs between control and responsibility might be worth it
    
- bind mounts, volumes & copy
    - development
        - containers should encapsulate the runtime environment but not necessarily the code
        - use ‘bind mounts’ to provide your local host project files to the running container
        - allows for instant updates without restarting the container
    - production
        - container should really work standalone, you should not have source code on your remove machine (image/container is the single source of truth)
        - use COPY instead of bind mounts to copy a code snapshot into the image
        - ensures that every image runs without any extra, surrounding configuration or code        