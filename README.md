https://kubernetes.io/docs/tasks/configure-pod-container/configure-persistent-volume-storage/

## Usage

```shell
minikube ssh
mkdir /mnt/data
echo 'Hello from Kubernetes storage' > /mnt/data/index.html
```

```shell
kubectl create -f pv-volume.yaml
kubectl create -f pv-claim.yaml
kubectl create -f pv-pod.yaml
kubectl create -f pv-service.yaml
kubectl get pod,services
kubectl describe service/task-pv-service

```


## test exposed ports
```shell
export POD_IP=$(kubectl describe service/task-pv-service | grep "Endpoints:" | awk '{print $2}')
curl $POD_IP

export CLUSTER_IP=$(kubectl describe service/task-pv-service | grep "IP:" | awk '{print $2}')
curl $CLUSTER_IP:8080
```

## check volume storage inside pod
```shell
kubectl exec -it task-pv-pod -- /bin/bash
ls /usr/share/nginx/html
exit
```