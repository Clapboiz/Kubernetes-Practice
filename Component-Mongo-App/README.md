## SET UP
```
kubectl create namespace kubernetes-dashboard
```

```
kubectl apply -f mongo-configmap.yaml 
```

```
kubectl apply -f mongo-express.yaml 
```

```
kubectl apply -f mongo-secret.yaml
```

```
kubectl apply -f mongo.yaml  
```

```
kubectl apply -f dashboard-ingress.yaml
```