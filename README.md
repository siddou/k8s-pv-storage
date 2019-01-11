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
curl localhost
```