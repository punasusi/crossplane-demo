```bash
kubectl crossplane build configuration \
    --name k8s

kubectl crossplane push configuration \
    punasusi/crossplane-k8s:v0.0.7
```


Note: need to be logged into docker to push repo there. Other repositories possible, but dockerhub is the default.