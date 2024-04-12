## Create an EKS Cluster

photos here with names

## Install ArgoCD

**https://argo-cd.readthedocs.io/en/stable/getting_started/#1-install-argo-cd**

```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

## Change Service Type to Load Balancer

**https://argo-cd.readthedocs.io/en/stable/getting_started/#service-type-load-balancer**

```
kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'
```

## Get the Admin Passcode

```
kubectl get secret argocd-initial-admin-secret -n argocd -o yaml
echo "value" | base64 --decode
```
