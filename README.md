# Sample Application — Nginx Web Server

A production-ready Kubernetes deployment managed by AGIE GitOps.

## Structure

```
base/              # Base Kubernetes manifests
  namespace.yaml   # App namespace
  deployment.yaml  # Nginx deployment (3 replicas)
  service.yaml     # ClusterIP + NodePort service
  configmap.yaml   # Custom nginx config + index page
  kustomization.yaml

overlays/
  dev/             # Development overrides (1 replica)
  staging/         # Staging overrides (2 replicas)
  production/      # Production overrides (3 replicas, resources)
```

## Deploying

```bash
# Dev environment
kubectl apply -k overlays/dev

# Staging
kubectl apply -k overlays/staging

# Production
kubectl apply -k overlays/production
```

## Managed by AGIE GitOps
This repository is automatically polled, synced, and deployed by the AGIE platform.
Changes pushed here will be automatically detected and applied to the target cluster.
