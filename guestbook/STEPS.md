## Quick Steps

### Kubernetes version: `1.0.2`

### Prerequisites

```bash
git clone https://github.com/pires/kubernetes-vagrant-coreos-cluster.git
cd kubernetes-vagrant-coreos-cluster
vagrant up
source ~/.bash_profile
```
#### NGINX Smoke test

```shell
$ kubectl run my-nginx --image=nginx --replicas=1 --port=80
$ kubectl get rc
$ kubectl get pods
$ kubectl expose rc my-nginx --port=80 --public-ip=192.168.222.7
```
Open browser at `http://192.168.222.7` to see NGINX homepage

#### Set Up

##### One Redis master

 - kubectl create -f redis-master-controller.yaml
 - kubectl get rc
 - kubectl get pods
 - kubectl create -f redis-master-service.yaml
 - kubectl get services

##### Two Redis slaves

 - kubectl create -f redis-slave-controller.yaml
 - kubectl get rc
 - kubectl get pods
 - kubectl create -f redis-slave-service.yaml
 - kubectl get services

##### Three frontends

 - kubectl create -f frontend-controller.yaml
 - kubectl get rc
 - kubectl get pods
 - kubectl create -f frontend-service.yaml
 - kubectl get services

#### Query

 - kubectl describe pods/`pod_name`
 - kubectl logs `pod_name`

#### Tear Down
 - kubectl stop rc -l "name in (redis-master, redis-slave, frontend)"
 - kubectl delete service -l "name in (redis-master, redis-slave, frontend)"

### Modifications

The `frontend-service.yaml` was modified to use `NodePort` to expose the service on all nodes on port: `30101`.

