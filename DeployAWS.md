## Deploy a cluster in AWS
```
kubectl create namespace punasusi-aws
```

```
kubectl --namespace punasusi-aws apply \
    --filename examples/aws-eks.yaml
```

Check deployment with:
```
kubectl get managed,releases,objects
```
