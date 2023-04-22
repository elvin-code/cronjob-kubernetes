# Simple cronjob - Python - Docker - kubernetes 

## Requirements

For building and running the application you need:

- [Python 3+](https://www.python.org/)
- [Docker](https://hub.docker.com/)
- [kubernetes](https://kubernetes.io/releases/download/#kubectl)


## Running the application locally

Using Dockerfile for build 
Dockerfile used to make image 

```shell
docker build -t simplejob .
```
This creates a Docker image from your Dockerfile script. You can now run your container, Verify is working 

```shell
docker run -it --rm simplejob:latest
```

Kubectl Create template for cronJob, with the image docker simplejob in file job.yaml

```shell
kubectl create cronjob simplejob --image=simplejob --schedule="0/5 * * * *" --dry-run=client -o  yaml > job.yaml
```

Apply kubectl cronjob 

```shell
kubectl apply -f job.yaml
```

Get list of cronjobs 

```shell
kubectl get cronjobs 
```

Wacth is a pod running

```shell
kubectl get pods  --watch
```

Get pods

```shell
kubectl get pods
```

Logs of pod name

```shell
kubectl logs {NAME_POD}
```