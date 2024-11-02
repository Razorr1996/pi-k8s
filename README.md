# Home Kubernetes Cluster on Raspberry Pi

## Installation
```shell
export INSTALL_K3S_VERSION=v1.31.2+k3s1
export INSTALL_K3S_EXEC='--flannel-backend=none --disable-network-policy --disable=servicelb --disable=traefik'

source .env # for K3S_TOKEN

curl -sfL https://get.k3s.io | sh -s - server
```

## Cilium installation
```shell
helm repo add cilium https://helm.cilium.io/
helm repo update

CILIUM_VERSION=1.16.3

helm diff upgrade cilium cilium/cilium \
  --version "${CILIUM_VERSION}" \
  --namespace kube-system \
  --values cilium-values.yaml

helm upgrade --install cilium cilium/cilium \
  --version "${CILIUM_VERSION}" \
  --namespace kube-system \
  --values cilium-values.yaml
```

## ArgoCD installation
```shell
helm repo add argo https://argoproj.github.io/argo-helm
helm repo update

helm upgrade --install argocd argo/argo-cd \
  --version 7.6.12 \
  --create-namespace \
  --namespace argocd \
  --values argocd-values.yaml
```

## Plan
- [x] Install k3s
- [x] Cilium
- [x] ArgoCD
- [ ] Cert Manager
- [ ] Ingress Controller
- [ ] Prometheus + Grafana
- [ ] Longhorn
- [ ] Loki
- ... Other apps
