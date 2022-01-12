# How to build the customized package

[From here](https://crossplane.io/docs/v1.5/getting-started/create-configuration.html) as well as [this](https://github.com/vfarcic/devops-toolkit-crossplane)


```bash
kubectl crossplane build configuration \
    --name k8s

kubectl crossplane push configuration \
    punasusi/crossplane-k8s:v0.0.21
```


Note: need to be logged into docker to push repo there. Other repositories possible, but dockerhub is the default.