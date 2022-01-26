```bash
kubectl crossplane build configuration \
    --name app

kubectl crossplane push configuration \
    punasusi/crossplane-app:v0.0.1
```