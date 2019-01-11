https://kubernetes.io/docs/tasks/configure-pod-container/configure-persistent-volume-storage/

## Usage

```shell
minikube ssh
mkdir /mnt/data
echo 'Hello from Kubernetes storage' > /mnt/data/index.html
```