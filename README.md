# kube-management

| Component     | version   | Compatiblity Doc |
| ------------- |:------:| :--------------: |
| Ubuntu        |   |  |
| Kubernetes    |   | [Kubernetes Dependencies - minimum version](https://github.com/kubernetes/kubernetes/blob/master/build/dependencies.yaml) |
| Containerd    |   | [Kubernetes Dependencies](https://github.com/kubernetes/kubernetes/blob/master/CHANGELOG/CHANGELOG-1.19.md#changed-11) |
| Calico        |   | [System Requirements](https://docs.projectcalico.org/archive/v3.16/getting-started/kubernetes/requirements) |
| CoreDNS       |   |  | [CoreDNS version in Kubernetes](https://github.com/coredns/deployment/blob/master/kubernetes/CoreDNS-k8s_version.md) |
| kube-state-metric |  | [Compatibility matrix](https://github.com/kubernetes/kube-state-metrics#compatibility-matrix) |
| Ingress       |        | [Changelog](https://github.com/kubernetes/ingress-nginx/blob/master/Changelog.md) |
| ceph-csi      |        | [Support Matrix](https://github.com/ceph/ceph-csi#support-matrix) |
| metric-server     |  | [Installation](https://github.com/kubernetes-sigs/metrics-server#installation) |
| prometheus-operator | | [Prerequisites](https://github.com/prometheus-operator/prometheus-operator#prerequisites) |
| node-exporter     |  |  |
| blackbox_exporter |  |  |
| Prometheus        |  |  |
| Keepalived    |   |  |
| HAProxy       |   |  |

## Checklist

### Add/Replace Master Node

### Add Worker Node

### Upgrade Cluster

### Security Checklist

### Create Namespace
* Add quota and limitrange
* Add network-policy

### Create user
* Namespace admin
* Cluster admin
* Release manager

### Update Certificates
* Renew api certificates
* Renew control-plane certificates
* Renew Kubelet certificates
* Renew etcd certificates
* Regenerate CA Key and Certificates
* Add new IP and Domain to certificates
* kubeadm phases may be useful
```
certs                        Certificate generation
  /ca                          Generate the self-signed Kubernetes CA to provision identities for other Kubernetes components
  /apiserver                   Generate the certificate for serving the Kubernetes API
  /apiserver-kubelet-client    Generate the certificate for the API server to connect to kubelet
  /front-proxy-ca              Generate the self-signed CA to provision identities for front proxy
  /front-proxy-client          Generate the certificate for the front proxy client
  /etcd-ca                     Generate the self-signed CA to provision identities for etcd
  /etcd-server                 Generate the certificate for serving etcd
  /etcd-peer                   Generate the certificate for etcd nodes to communicate with each other
  /etcd-healthcheck-client     Generate the certificate for liveness probes to healthcheck etcd
  /apiserver-etcd-client       Generate the certificate the apiserver uses to access etcd
  /sa                          Generate a private key for signing service account tokens along with its public key
kubeconfig                   Generate all kubeconfig files necessary to establish the control plane and the admin kubeconfig file
  /admin                       Generate a kubeconfig file for the admin to use and for kubeadm itself
  /kubelet                     Generate a kubeconfig file for the kubelet to use *only* for cluster bootstrapping purposes
  /controller-manager          Generate a kubeconfig file for the controller manager to use
  /scheduler                   Generate a kubeconfig file for the scheduler to use
...
upload-certs                 Upload certificates to kubeadm-certs
```


