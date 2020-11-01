# Run in kubernetes

## Use MS with Docker

[Install docker](https://docs.docker.com/install/)


## Use MS with Kubernetes locally

We create a extensive example an tutorial about use Python microservice scaffold with Kubernetes in this repository:
https://github.com/python-microservices/microservices-chat

In the next lines, you can find a simple tutorial tu run this microservice in a simple Kubernetes cluster

* Installing Kubernetes...

```bash
curl -Lo kubectl https://storage.googleapis.com/kubernetes-release/release/v1.9.0/bin/linux/amd64/kubectl && chmod +x kubectl && sudo mv kubectl /usr/local/bin/
```

* Installing Minikube...

```bash
curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/
```


Start minikube and set the environment of docker

```bash
minikube start
eval $(minikube docker-env)
kubectl config use-context minikube
```

If a shell isn't your friend. You could use kubernetes web panel to see your pods:

```bash
minikube dashboard
```

Create your image

```bash
docker build -t template:v1 .
```

Deploy your images locally:

```bash
kubectl apply -f service.yaml
minikube service template
```

Clean your environment

```bash
kubectl delete template
kubectl delete template
docker rmi template:v1 -f
minikube stop
eval $(minikube docker-env -u)
minikube delete
```