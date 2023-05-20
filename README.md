# Kubernetes Production Toolkit

Battle-tested Kubernetes utilities, operators, and configurations for production environments.

## Overview

This repository contains curated Kubernetes manifests, Helm charts, and utilities used in production-grade EKS and self-managed Kubernetes clusters.

## Components

### Core Infrastructure
- **cert-manager**: Automated certificate management with Let's Encrypt
- **external-dns**: Automatic DNS records for Kubernetes ingresses
- **cluster-autoscaler**: Pod-driven autoscaling for node groups
- **metrics-server**: Resource metrics for HPA and VPA

### Networking
- **aws-load-balancer-controller**: AWS ALB/NLB integration
- **nginx-ingress**: High-performance ingress controller
- **istio**: Service mesh for advanced traffic management
- **calico**: Network policies and security

### Observability
- **prometheus-operator**: Kubernetes-native monitoring
- **grafana**: Metrics visualization and dashboards
- **loki**: Log aggregation system
- **tempo**: Distributed tracing backend

### Security
- **kyverno**: Policy engine for Kubernetes
- **falco**: Runtime security monitoring
- **sealed-secrets**: Encrypted secrets management
- **trivy-operator**: Security scanning

### GitOps
- **argocd**: Declarative GitOps CD for Kubernetes
- **flux**: Continuous delivery with Helm and Kustomize

## Directory Structure

```
.
├── helm-charts/          # Custom Helm charts
├── operators/            # Kubernetes operators
├── manifests/            # Raw Kubernetes manifests
├── kustomize/            # Kustomize overlays
├── policies/             # Kyverno policies
└── examples/             # Example configurations
```

## Usage

### Prerequisites
- Kubernetes 1.24+
- Helm 3.8+
- kubectl 1.24+

### Quick Start

```bash
# Install core components
kubectl apply -f manifests/core/

# Install monitoring stack
helm install prometheus-stack helm-charts/kube-prometheus-stack/

# Deploy ArgoCD
kubectl create namespace argocd
kubectl apply -n argocd -f manifests/argocd/
```

## Best Practices

1. **Resource Limits**: All workloads have CPU and memory limits
2. **Pod Disruption Budgets**: Critical services use PDBs
3. **Network Policies**: Zero-trust networking by default
4. **RBAC**: Least privilege access controls
5. **Image Security**: All images scanned and signed

## Production Considerations

- Multi-AZ deployments for high availability
- Automated backup strategies
- Disaster recovery procedures
- Monitoring and alerting
- Cost optimization with spot instances

## Author

Andrés Muñoz - Principal DevOps Architect
Specialized in Kubernetes, EKS, and cloud-native architectures

## License

MIT License
