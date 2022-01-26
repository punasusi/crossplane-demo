## Deploy a cluster in AWS
```
kubectl create namespace cpdemo
```

```
kubectl --namespace cpdemo apply \
    --filename examples/aws-eks.yaml
```

Check deployment with:
```
kubectl get managed
kubectl get all --namespace cpdemo
```
