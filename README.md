# rpc-example

this example use go-zero rpc framework,deploy use k8s


# deploy in minikube

1.check minikube registry

```
minikube addons list
```

```
minikube addons enable registry
```

load image into minikube

```
 minikube image load server:v1
 minikube image load client:v1
```

deploy server and client

```
kubectl apply -f server.yaml
kubectl apply -f client.yaml
```
