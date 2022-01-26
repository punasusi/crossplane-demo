
## Install crossplane
[Taken from here](https://crossplane.io/docs/v1.5/getting-started/install-configure.html)

First, a management/host kubernetes cluster is needed. 
Then: 
```
kubectl create namespace crossplane-system
helm repo add crossplane-stable https://charts.crossplane.io/stable
helm repo update

helm install crossplane --namespace crossplane-system crossplane-stable/crossplane

helm list -n crossplane-system

kubectl get all -n crossplane-system
```

## Setup Crossplane
```
kubectl apply \
    --filename crossplane-config/provider-kubernetes.yaml

kubectl apply \
    --filename crossplane-config/config-app.yaml
```

```
kubectl get pkgrev
```
Wait for packages to be ready





