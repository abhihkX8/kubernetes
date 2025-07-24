# kubernetes

Welcome to the `kubernetes` repository!

This project provides resources, manifests, and scripts for working with Kubernetes—an open-source platform for automating deployment, scaling, and management of containerized applications.

## Table of Contents

- [About](#about)
- [Features](#features)
- [Getting Started](#getting-started)
- [Setting Up a Local Kubernetes Cluster with kind](#setting-up-a-local-kubernetes-cluster-with-kind)
- [Understanding Namespaces](#understanding-namespaces)
- [About Services in Kubernetes](#about-services-in-kubernetes)
- [Using kubectl](#using-kubectl)
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

[kind](https://kind.sigs.k8s.io/) (Kubernetes IN Docker) lets you run Kubernetes clusters locally using Docker containers as nodes.

### Prerequisites

- [Docker](https://docs.docker.com/get-docker/) installed on your system

### Installation

Install kind (Linux/macOS):

```bash
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.23.0/kind-$(uname)-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind
```

### Create a Cluster

```bash
kind create cluster --name my-cluster
```

To view your clusters:

```bash
kind get clusters
```

To delete a cluster:

```bash
kind delete cluster --name my-cluster
```

---

## Understanding Namespaces

Namespaces in Kubernetes provide a way to divide cluster resources between multiple users or teams. They are useful for:

- Organizing resources for different environments (dev, staging, prod)
- Avoiding name collisions

Create a namespace:

```bash
kubectl create namespace dev
```

Use a namespace:

```bash
kubectl config set-context --current --namespace=dev
```

List all namespaces:

```bash
kubectl get namespaces
```

---

## About Services in Kubernetes

Services in Kubernetes expose your applications running on a set of Pods as a network service. Types include:

- **ClusterIP**: (default) Exposes the service on an internal IP in the cluster.
- **NodePort**: Exposes the service on each Node’s IP at a static port.
- **LoadBalancer**: Exposes the service externally using a cloud provider’s load balancer.
- **ExternalName**: Maps the service to the contents of the externalName field (e.g., DNS name).

Example Service manifest:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-service
spec:
  selector:
    app: MyApp
  ports:
    - protocol: TCP
      port: 80
      targetPort: 9376
  type: ClusterIP
```

Apply the service:

```bash
kubectl apply -f manifests/my-service.yaml
```

---

## Using kubectl

[kubectl](https://kubernetes.io/docs/reference/kubectl/) is the command-line tool for interacting with your Kubernetes cluster.

Common commands:

- View all pods:  
  ```bash
  kubectl get pods
  ```
- View all resources in a namespace:  
  ```bash
  kubectl get all -n <namespace>
  ```
- Describe a deployment:  
  ```bash
  kubectl describe deployment <deployment-name>
  ```
- Apply a manifest:  
  ```bash
  kubectl apply -f <file.yaml>
  ```
- Delete a resource:  
  ```bash
  kubectl delete -f <file.yaml>
  ```

---

## Contributing

Contributions are welcome! Please open an issue or submit a pull request for improvements or new features.

1. Fork the repo
2. Create your feature branch (`git checkout -b feature/YourFeature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin feature/YourFeature`)
5. Open a Pull Request

---

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

## Contact

Maintainer: [abhihkX8](https://github.com/abhihkX8)

For questions or support, open an issue in this repository.

---

Happy Kubernetes-ing! 🚀
