# Home Kubernetes Cluster on Raspberry Pi

## Installation
```shell
export INSTALL_K3S_VERSION=v1.31.1+k3s1
export INSTALL_K3S_EXEC='--flannel-backend=none --disable-network-policy --disable=servicelb --disable=traefik'

source .env # for K3S_TOKEN

curl -sfL https://get.k3s.io | sh -s - server
```
