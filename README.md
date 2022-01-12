# crossplane-demo

Notes and configs on the demo of crossplane

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
## Setup Azure
Replace {SubID} and {ResourceGroup} with correct values for the resource group you will use
```
az ad sp create-for-rbac --name crossplane-demo --scopes /subscriptions/ {SubID}/resourceGroups/{ResourceGroup} > azure_creds.json
```

Add as a secret:
```
kubectl create secret generic azure-creds -n crossplane-system --from-file=azure_creds.json
```

## Setup AWS

Replace `[...]` with your access key ID`
```
export AWS_ACCESS_KEY_ID=[...]
```
Replace `[...]` with your secret access key
```
export AWS_SECRET_ACCESS_KEY=[...]

echo "[default]
aws_access_key_id = $AWS_ACCESS_KEY_ID
aws_secret_access_key = $AWS_SECRET_ACCESS_KEY
" >aws-creds.conf

kubectl --namespace crossplane-system \
    create secret generic aws-creds \
    --from-file creds=./aws-creds.conf
```
## Setup Crossplane
```
kubectl apply \
    --filename crossplane-config/provider-aws.yaml
kubectl apply \
    --filename crossplane-config/provider-azure.yaml
kubectl apply \
    --filename crossplane-config/provider-helm.yaml
kubectl apply \
    --filename crossplane-config/provider-kubernetes.yaml
```
Check output of:
```
kubectl get pkgrev
```
to see when providers are healthy, and can be configured with the next steps

```
kubectl apply \
    --filename crossplane-config/provider-config-aws.yaml
```
```
kubectl apply \
    --filename crossplane-config/provider-config-azure.yaml
```
Might need to retry this command if 'not recognized' as the above provider is not yet ready

```
kubectl apply \
    --filename crossplane-config/config-k8s.yaml
```

```
kubectl get pkgrev
```
Wait for packages to be ready





