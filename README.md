# Exercise-01-EKS-GitOps

## Project Overview

This project demonstrates a complete GitOps-based application deployment on Amazon EKS using ArgoCD. Instead of deploying applications manually with `kubectl`, the Kubernetes manifests are stored in GitHub, and ArgoCD continuously monitors the repository to synchronize the desired state with the EKS cluster.

This exercise demonstrates a production-style GitOps workflow used in modern Kubernetes environments.

---

## Architecture

```
Developer
    │
    ▼
Git Push
    │
    ▼
GitHub Repository
    │
    ▼
ArgoCD
    │
    ▼
Amazon EKS Cluster
    │
    ▼
Deployment → ReplicaSet → Pods
               │
               ▼
          ClusterIP Service
```

---

## Tech Stack

* Amazon EKS
* Kubernetes
* ArgoCD
* Git
* GitHub
* YAML
* NGINX

---

## Project Workflow

1. Created an Amazon EKS cluster.
2. Developed Kubernetes Deployment and Service manifests.
3. Deployed the application to the EKS cluster.
4. Installed and configured ArgoCD.
5. Created a GitHub repository for Kubernetes manifests.
6. Connected ArgoCD to the GitHub repository.
7. Enabled automatic synchronization with self-healing.
8. Updated the deployment replica count from 2 to 3.
9. Pushed the change to GitHub.
10. Verified that ArgoCD automatically synchronized the change and scaled the application without manual intervention.

---

## Kubernetes Resources

* Deployment
* ReplicaSet
* Pods
* ClusterIP Service

---

## GitOps Validation

The deployment initially ran with **2 replicas**.

After updating the manifest to **3 replicas** and pushing the change to GitHub, ArgoCD automatically detected the new commit and synchronized the EKS cluster.

Deployment events confirmed that the ReplicaSet was automatically scaled from **2 to 3 replicas**, demonstrating a successful GitOps workflow.

---

## Key Learning Outcomes

* Amazon EKS cluster management
* Kubernetes Deployment and Service creation
* GitOps workflow implementation
* ArgoCD installation and configuration
* Automatic synchronization
* Self-healing deployment management
* Declarative infrastructure using Kubernetes manifests
* Production-style continuous deployment

---

## Commands Used

```bash
kubectl get nodes
kubectl get deployment,pods,svc
kubectl get pods -n argocd
kubectl describe deployment payment-service
git log --oneline
```

---

## Project Outcome

Successfully implemented an end-to-end GitOps deployment pipeline where every application change is managed through GitHub and automatically synchronized to Amazon EKS by ArgoCD. The project demonstrates modern Kubernetes deployment practices and production-oriented GitOps automation.
