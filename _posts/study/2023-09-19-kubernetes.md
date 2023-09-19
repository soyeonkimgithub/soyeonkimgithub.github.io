---
layout: post
title: Docker 
categories: study
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