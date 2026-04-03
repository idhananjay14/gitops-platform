# 🚀 GitOps Kubernetes Platform

## Overview

This project demonstrates a GitOps-based Kubernetes platform using ArgoCD. It implements automated deployments, drift detection, and self-healing mechanisms, along with observability using Prometheus and Grafana.

---

## Architecture

```
GitHub (Source of Truth)
        ↓
ArgoCD (GitOps Controller)
        ↓
Kubernetes Cluster (Kind)
        ↓
Node.js Application
        ↓
Prometheus and Grafana (Monitoring)
```

---

## Tech Stack

* Kubernetes (Kind)
* ArgoCD
* Docker
* Node.js (Express)
* Prometheus
* Grafana

---

## Key Features

* Git as the single source of truth
* Automated synchronization and deployment via ArgoCD
* Self-healing infrastructure (automatic drift correction)
* Drift detection (pod deletion, scaling changes)
* Real-time monitoring (CPU, memory, system metrics)
* Custom dark-themed user interface

---

## GitOps Workflow

1. Code is pushed to GitHub
2. ArgoCD detects repository changes
3. Kubernetes manifests are synchronized
4. Cluster state is updated automatically
5. Any configuration drift is reconciled

---

## Drift Test Results

* Pod deletion → automatically recovered (~20 seconds)
* Manual scaling → reverted to desired state (~45 seconds)

---

## Monitoring

* Prometheus collects metrics from the cluster
* Grafana provides visualization dashboards
* Node Exporter exposes system-level metrics

---

## Quick Start

```bash
git clone https://github.com/idhananjay14/gitops-platform.git
cd gitops-platform

kind create cluster --name gitops-cluster

kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

kubectl apply -f manifests/

kubectl port-forward svc/gitops-app-service -n gitops-platform 8095:80
```

Access the application at: http://localhost:8095

---

## Screenshots

![Application UI](demo/screenshots/2-app-ui.png)
![ArgoCD Sync Status](demo/screenshots/3-argocd-synced.png)
![Drift Detection](demo/screenshots/5-scale-drift.png)
![Grafana Dashboard](demo/screenshots/7-grafana.png)

---

## Key Learnings

* GitOps principles and workflow
* Kubernetes deployment lifecycle
* Drift detection and reconciliation
* Observability using Prometheus and Grafana

---

## Author

Dhananjay Bhardwaj
