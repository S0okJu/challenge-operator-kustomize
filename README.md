# Challenge Operator Kustomize

## Introduction
A Kustomize for deploying challenge operator. 


## Project Structure

```
challenge-operator-kustomize/
├── challenge-operator/
│   ├── base/                    # Base Kubernetes manifests
│   │   ├── cluster-role.yaml
│   │   ├── cluster-role-binding.yaml
│   │   ├── deployment.yaml
│   │   ├── kustomization.yaml
│   │   ├── metrics-service.yaml
│   │   ├── service-account.yaml
│   │   └── servicemonitor.yaml
│   └── overlays/
│       └── dev/                 # Development environment overlay
│           ├── config/          # Environment-specific configs (ex. Database, Queue)
│           └── kustomization.yaml
└── README.md
```

## Components

### Base Configuration (`base/`)

The base directory contains the core Kubernetes manifests for the challenge operator:

- **deployment.yaml**: Kubernetes operator deployment with security context and volume mounts
- **service-account.yaml**: Service account for the operator
- **cluster-role.yaml**: RBAC permissions for the operator
- **cluster-role-binding.yaml**: Binds the service account to the cluster role
- **metrics-service.yaml**: Service for exposing metrics
- **servicemonitor.yaml**: Prometheus ServiceMonitor for metrics collection. 

### Overlays (`overlays/`)

Environment-specific configurations that customize the base manifests:

- **dev/**: Development environment configuration
  - Customizes image registry
  - Generates secrets from environment files: Databse, Queue
