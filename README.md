## Selected Examples that run on coreos VMs

### Kubernetes version: `1.0.2`

### Prerequisites

```bash
git clone https://github.com/pires/kubernetes-vagrant-coreos-cluster.git
cd kubernetes-vagrant-coreos-cluster
vagrant up
source ~/.bash_profile
```
Three coreos VMs are stood up by vagrant:

 - master `172.17.8.101`
 - node-01 `172.17.8.102`
 - node-02 `172.17.8.103`

Original examples are from https://github.com/kubernetes/kubernetes/tree/v1.0.2/examples
