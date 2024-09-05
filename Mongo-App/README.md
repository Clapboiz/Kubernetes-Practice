# MONGO APP
This app uses minikube (1 cluster, 1 node)

# SET UP
Follow these step. 

```
kubectl apply -f mongo-config.yaml
```

```
kubectl apply -f mongo-secret.yaml 
```

```
kubectl apply -f mongo.yaml 
```

```
kubectl apply -f webapp.yaml 
```

```
kubectl get all
```


```
minikube service webapp-service
```