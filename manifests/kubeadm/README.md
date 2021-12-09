# Deploy Kubernetes with kubeadm
## Setup api loadbalancer
...


## Initial Clusters
```
# kubeadm init \
 --config kubadm-init.conf \
 --upload-certs \
 --patches patches/ \
```

## Join Control-Plane node
```
# kubeadm join --config kubeadm-join-controleplane.yml \
 --ignore-preflight-errors=DirAvailable--etc-kubernetes-manifests
 --patches patches/
```

## Join New worker node
```
# kubeadm join --config kubeadm-join.yml
```
