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

## Vault

Vault runs in standalone mode with `file` storage on the NFS share (`/container_data/vault`).

One-time setup on the NFS export: `mkdir -p /container_data/vault && chown 100:1000 /container_data/vault`

First run (save the output, it is shown only once):

```
kubectl exec -n <namespace> vault-0 -- vault operator init
```

After every pod restart or power outage Vault starts sealed. Unseal with three of the keys:

```
kubectl exec -it -n <namespace> vault-0 -- vault operator unseal
```
