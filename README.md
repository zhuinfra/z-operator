# Z-Operator

A Kubernetes Operator demo project built with Kubebuilder.

## Description

This is a Kubernetes Operator project that demonstrates how to build, deploy, and manage custom resources on Kubernetes clusters.

## Prerequisites

- Go 1.21+
- Docker
- kubectl
- Kubebuilder v3+

## Getting Started

### Install Kubebuilder

```bash
# macOS
brew install kubebuilder

# Linux
curl -L -o kubebuilder https://go.kubebuilder.io/dl/latest/$(go env GOOS)/$(go env GOARCH)
chmod +x kubebuilder && mv kubebuilder /usr/local/bin/
```

### Initialize Project

```bash
# Initialize the project with domain and repo
kubebuilder init --domain zhuinfra.com --repo github.com/zhuinfra/z-operator

# Create API and Controller
kubebuilder create api --group demo --version v1 --kind DemoResource
```

### Build and Deploy

```bash
# Install CRDs
make install

# Run the controller locally
make run

# Build and push Docker image
make docker-build docker-push IMG=<your-registry>/z-operator:tag

# Deploy to cluster
make deploy IMG=<your-registry>/z-operator:tag
```

## Project Structure

```
├── config/             # Kubernetes YAML configs
├── cmd/                # Main entrypoint
├── api/                # API definitions
├── internal/           # Controller logic
├── Dockerfile          # Container image build
├── Makefile            # Build targets
└── PROJECT             # Kubebuilder metadata
```

## License

Copyright 2026 zhuinfra.