# kubernetes

Welcome to the `kubernetes` repository!

This project provides resources, manifests, and scripts for working with Kubernetes—an open-source platform for automating deployment, scaling, and management of containerized applications.

## Table of Contents

- [About](#about)
- [Features](#features)
- [Getting Started](#getting-started)
- [Setting Up a Local Kubernetes Cluster with kind](#setting-up-a-local-kubernetes-cluster-with-kind)
- [Kubernetes Concepts and Commands](#kubernetes-concepts-and-commands)
  - [kubectl](#kubectl)
  - [Namespaces](#namespaces)
  - [Pods](#pods)
  - [Deployments](#deployments)
  - [Services](#services)
  - [Port Forwarding](#port-forwarding)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## About

This repository contains:

- Kubernetes YAML manifests for various resources (Deployments, Services, Namespaces, etc.)
- Scripts for cluster setup, upgrades, and management (with a focus on local clusters using [kind](https://kind.sigs.k8s.io/))
- Examples for common deployment patterns
- Documentation and best practices for Kubernetes

## Features

- Ready-to-use manifests for deploying and exposing applications
- Scripts for automating cluster creation with kind (Kubernetes IN Docker)
- Sample namespace management and service configuration
- Guidance on using kubectl for cluster management

## Getting Started

Clone this repository:

```bash
git clone https://github.com/abhihkX8/kubernetes.git
cd kubernetes
```

---

## Setting Up a Local Kubernetes Cluster with kind

[kind](https://kind.sigs.k8s.io/) (Kubernetes IN Docker) allows you to run Kubernetes clusters locally using Docker containers as nodes. It's useful for development and testing purposes. To get started:

- **Install Docker** on your system.
- **Download and install kind** on your machine.
- **Create a cluster:**  
  `kind create cluster --name <cluster-name>`
- **List clusters:**  
  `kind get clusters`
- **Delete a cluster:**  
  `kind delete cluster --name <cluster-name>`
- After cluster creation, your local `kubectl` will be automatically configured to interact with the kind cluster.

---

## Kubernetes Concepts and Commands

### kubectl

`kubectl` is the command-line tool for interacting with your Kubernetes cluster. It allows you to deploy applications, inspect and manage cluster resources, and view logs. Mastering `kubectl` is essential for efficient Kubernetes management.

**Common kubectl commands:**
- Check version:  
  `kubectl version`
- View cluster info:  
  `kubectl cluster-info`
- Apply resource from a manifest:  
  `kubectl apply -f <file.yaml>`
- Delete a resource:  
  `kubectl delete -f <file.yaml>`
- Get all resources:  
  `kubectl get all`
- View logs:  
  `kubectl logs <pod-name>`

### Namespaces

Namespaces provide a way to organize resources within a Kubernetes cluster. They allow you to isolate resources for different projects or teams, and help prevent name collisions. You can use namespaces to manage environments such as development, testing, and production.

**Namespace commands:**
- Create a namespace:  
  `kubectl create namespace <namespace>`
- List all namespaces:  
  `kubectl get namespaces`
- Set default namespace for your context:  
  `kubectl config set-context --current --namespace=<namespace>`
- View resources in a namespace:  
  `kubectl get all -n <namespace>`

### Pods

A Pod is the smallest deployable unit in Kubernetes and represents a single instance of a running process. Pods can contain one or more containers that share the same network and storage.

**Pod commands:**
- List pods:  
  `kubectl get pods`
- Get detailed info:  
  `kubectl describe pod <pod-name>`
- Delete a pod:  
  `kubectl delete pod <pod-name>`
- View logs of a pod:  
  `kubectl logs <pod-name>`

### Deployments

A Deployment manages a set of identical pods, ensuring that the desired number are running and available. Deployments are used for rolling updates, rollbacks, and scaling applications.

**Deployment commands:**
- List deployments:  
  `kubectl get deployments`
- Describe a deployment:  
  `kubectl describe deployment <deployment-name>`
- Scale a deployment:  
  `kubectl scale deployment <deployment-name> --replicas=<number>`
- Roll out a new version:  
  `kubectl rollout restart deployment/<deployment-name>`
- Check rollout status:  
  `kubectl rollout status deployment/<deployment-name>`

### Services

Services provide stable networking endpoints to access pods. They abstract a set of pods and enable discovery and communication within (and sometimes outside) the cluster. Types of services include ClusterIP, NodePort, and LoadBalancer.

**Service commands:**
- List services:  
  `kubectl get services`
- Describe a service:  
  `kubectl describe service <service-name>`
- Expose a deployment as a service:  
  `kubectl expose deployment <deployment-name> --type=<service-type> --port=<port>`

### Port Forwarding

Port forwarding allows you to access your Kubernetes applications from your local machine without exposing them externally. This is especially useful for debugging.

**Port forwarding commands:**
- Forward a pod’s port to your local machine:  
  `kubectl port-forward pod/<pod-name> <local-port>:<pod-port>`
- Forward a service’s port:  
  `kubectl port-forward service/<service-name> <local-port>:<service-port>`

---

## Contributing

Contributions are welcome! Please open an issue or submit a pull request for improvements or new features.

1. Fork the repo
2. Create your feature branch (`git checkout -b feature/YourFeature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin feature/YourFeature`)
5. Open a Pull Request

---


## Contact

Maintainer: [abhihkX8](https://github.com/abhihkX8)

For questions or support, open an issue in this repository.

---

Happy Kubernetes-ing! 🚀
