# Docker Orchestration

```bash
$ docker run nodejs
```

```bash
$ docker service create --replicas=100 nodejs
```

* Docker Swarm
* Kubernetes
* MESOS

### Docker Swarm
```bash
$ docker service create --replicas=3 --network frontend my-web-server
$ docker service create --replicas=3 8080:80 my-web-server
$ docker service create --replicas=3 my-web-server
```

### Kubernetes


### Kubectl
```bash
$ kubectl run hello-minikube
```

```bash
$ kubectl cluster-info
```

```bash
$ kubectl get nodes
```

```bash
$ kubectl run my-web-app --image=my-web-app --replicas=100
```