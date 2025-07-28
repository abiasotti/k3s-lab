# k3s-lab

A GitOps-style home lab deployment for my K3s cluster.  
This repo manages Kubernetes manifests, Helm values, and ArgoCD Applications for various services running in my lab environment.

---

## 📦 Structure

```text
.
├── argocd/           # ArgoCD Application definitions (App of Apps, individual apps)
├── apps/             # Kustomize/manifest files for deployed apps
├── helm/             # Helm values and overrides for templated apps
├── secrets/          # SealedSecrets or Vault policies (if used)
├── scripts/          # Bootstrap/setup scripts
└── README.md         # You're here
