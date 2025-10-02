# Alpine K8s Dockerfile

A lightweight Kubernetes development environment using Alpine Linux and Kind, perfect for local testing and development.

<img width="800" height="472" alt="Image" src="https://github.com/user-attachments/assets/73dd0ffa-095d-461f-92de-c8321526bcc4" />

## Quick Start

```bash
# Build image
docker build -t k8s-dev .

# Run container
docker run -it \
  --privileged \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v $(pwd):/workspace \
  -v $HOME/.kube:/root/.kube \
  k8s-dev

# Create multi-node cluster
kind create cluster --config multi-cluster.yaml --name my-multi-cluster

# Share kubeconfig with host
kind get kubeconfig --name my-cluster > ~/.kube/config
```

## Features
- Alpine Linux based (~10MB base image)
- Built-in k8s tools (kubectl, kind, helm, k9s)
- Local machine integration
- Single/Multi-node cluster support
- VSCode Kubernetes extension ready
