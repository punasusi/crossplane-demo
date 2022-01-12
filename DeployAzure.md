
## Deploy a cluster in Azure
```
kubectl create namespace punasusi-azure
```

```
kubectl --namespace punasusi-azure apply \
    --filename examples/azure-aks.yaml
```

and check deployment with:
```
kubectl get managed,releases,objects
```
