---
layout: post
title: Docker 
categories: machine learning
sitemap: false
hide_last_modified: true
published: true
---

## [Kubernetes] Docker and Kubernetes: The Practice Guide - Kubernetes

## Kubernetes

### Why?

- manual deployment of containers is hard to maintain, error-prone and annoying
    - container might crash/go down and need to be replaced
    - might need more container instances on traffic spikes
    - incoming traffic should be distributed equally
- services like AWS ECS can help → but that locks us in!
    - container health checks + automatic re-deployment
    - autoscaling
    - load balancer
- Kubernetes help us

### What?

- an open-source system (de-facto standard) for orchestrating container deployments
- automatic deployment, scaling and load balancing, management
    - Kubernetes configuration → provider specific setup → any cloud provider
    - standardised way of describing the to-be-created and to-be-managed resources of the Kubernetes Cluster
    - cloud-provider-specific settings ca be added
- Kubernetes is responsible for managing your deployed application for ensuring that your application  runs the way it should run, that your containers are running and reachable by your end users.
    - create your objects (i.e. Pods) and manage them
    - monitor Pods and re-create them, scale Pods etc.
    - utilise the provided (cloud) resources to apply your configuration / goals
- Kubernetes does not
    - take care of infrastructure your application needs
    - create the Cluster and the Node instances (Worker + Master Nodes)
    - setup API server, kubelet and other Kubernetes services/software on Nodes
    - create other (cloud) provider resources that might be needed (i.e. load balancer, file systems)
- Kubernetes is like Docker-Compose for multiple machines.

### Concepts

- Cluster: a set of Node machines which are running the containerised application(Worker Nodes) or control other Nodes(Master Node)
- Nodes: physical or virtual machine with a certain hardware capacity which hosts one or multiple Pods and communicates with the Cluster
    - Master Node: cluster control plane, managing the Pods across Worker Nodes
    - Worker Node: hosts pods, running app containers (+resources)
- Pods: hold the actual running App Containers + their required resources (i.e. volumes)
- Containers: Normal (Docker) Containers
- Services: logical set of Pods with a unique, Prod- and Container- independent IP address
- Worker Node
    - Worker Node > Pod(Container(s), volumes) + Proxy/Config
    - Worker Nodes run the containers of your application.
    - Worker Nodes → your computer
    - Worker Nodes(kubelet, Docker, Pod, kube-proxy)
    - “Nodes” are your machine/virtual instances.
    - Multiple Pods can be created and removed to scale your app
- Master Node
    - consists of,
    1. API Server → API for the kubelets to communicate
    2. Scheduler → Watches for new Pods, selects Worker Nodes to run them on
    3. Kube-Controller-Manager → Watches and controls Worker Nodes, correct number of Pods
    4. Cloud-Controller-Manager → Like Kube-Controller-Manager but for a specific cloud provider: knows how to interact with cloud provider resources
    - Master Node > The Control Plane + Various components which help with managing the Worker Nodes
    - Master Node controls your deployment (i.e. all Worker Nodes)
    - Master Node sends instructions to Cloud Provider API

### Installation

- Cluster - Master Node, Work Node(s), also install all required software(services)
- kubectl - a tool for sending instructions to the cluster (i.e. new deployment)
- Minikube - tool that makes it easy to run Kubernetes locally, runs a single-node Kubernetes cluster inside a virtual machine

### Objects

- Kubernetes works with Objects - Pods, Deployments, Services, Volumes, etc.
- Objects can be created in two ways Imperatively or Declaratively
    - Imperatively: kubectl cerate deployment … (like each docker run command)
    - Declaratively: kubectl apply -f config.yaml (like docker-compose)
- Pod
    - smallest unit Kubernetes interacts with
    - containers and runs one or multiple containers: most common use-case is ‘one container per Pod’
    - contain shared resources (i.e. volumes) for all Pod containers
    - has a cluster-internal IP by default: containers inside a Pod can communicate via localhost
    - Pods are designed to be ephemeral: Kubernetes will start, stop and replace them as needed
    - For Pods to be managed for you, you need a ‘controller’ (i.e. a ‘Deployment’)
- Deployments
    - controls (multiple) Pods
    - you set a desired state, Kubernetes then changes the actual state: define which Pods and containers to run and the number of instances
    - deployments can be paused, deleted and rolled back
    - deployments can be scaled dynamically (and automatically): you can change the number of desired Pods as needed
    - Deployments manage a Pod for you, you can also create multiple Deployments.
    - You therefore typically don’t directly control Pods, instead you use Deployments to set up the desired end state.
- Auth error when kubectl to connect docker hub
    - login docker in console then,
    - kubectl create secret generic regcred --from-file=.dockerconfigjson=/Users/soyeonkim/.docker/config.json --type=[kubernetes.io/dockerconfigjson](http://kubernetes.io/dockerconfigjson)
    - kubectl create secret docker-registry regcred --docker-server=https://index.docker.io/v1/ --docker-username=soyeonsophiekim --docker-password=XXX [-docker-email=sophie.kim.it@gmail.com](mailto:--docker-email=sophie.kim.it@gmail.com)
    - if there is already, kubectl delete secret regcred
    - confirm it’s created, kubectl get secret regcred --output=yaml
    - ref. https://kubernetes.io/docs/tasks/configure-pod-container/pull-image-private-registry/
- Service
    - exposes Pods to the Cluster or Externally
    - Pods have an internal IP by default and it changes when a Pod is replaced: finding Pods is hard if the IP changes all the time
    - Services group Pods with a shared IP
    - Services can allow external access to Pods: the default (internal only) can be overwritten
    - Without Services, Pods are very hard to reach and communication is difficult
    - Reaching a Pod from outside the Cluster is not possible at all without Services.
- Volumes
    - State is data created and used by your application which must not be lost
        - User-generated data, user accounts etc → stored in a db or files
        - Intermediate results derived by the app → stored in memory, temporary files
        - Volumes can be solution!
    - Kubernetes can mount Volumes into Containers
        → variety type : Local volumes, cloud-provider specific volumes
        → volume lifetime depends on the Pod lifetime: container restart then volumes are survive, Pods are destroyed then volumes removed
        
    - Persistent Volumes
        → Volumes are destroyed when a Pod is removed
        → Pod- and Node-independent Volumes are sometimes required
        → Cluster > Node > Pod1, Pod2, .. PV Claim ↔ PV(Persistent Volume)