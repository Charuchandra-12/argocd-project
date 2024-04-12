## Create an EKS Cluster

**Create roles for EKS and EC2**

![alt text](<project-pics/Screenshot 2024-04-12 at 12.30.42 PM.png>)
![alt text](<project-pics/Screenshot 2024-04-12 at 12.31.21 PM.png>)
![alt text](<project-pics/Screenshot 2024-04-12 at 12.32.30 PM.png>)
![alt text](<project-pics/Screenshot 2024-04-12 at 12.39.16 PM.png>)

**Create k8s cluster and node group**

![alt text](<project-pics/Screenshot 2024-04-12 at 1.01.54 PM.png>)
![alt text](<project-pics/Screenshot 2024-04-12 at 1.07.59 PM.png>)

**Configure cloudshell to connect to our EKS cluster**

![alt text](<project-pics/Screenshot 2024-04-12 at 1.12.52 PM.png>)

**Install the ArgoCD in K8s cluster**

![alt text](<project-pics/Screenshot 2024-04-12 at 1.15.54 PM.png>)

**Configure ArgoCD to access it publicly**

![alt text](<project-pics/Screenshot 2024-04-12 at 1.21.00 PM.png>)

**Get the passcode for the ArgoCD**

![alt text](<project-pics/Screenshot 2024-04-12 at 1.22.23 PM.png>)

**Connect the ArgoCD to git repo for the k8s manifests**

![alt text](<project-pics/Screenshot 2024-04-12 at 1.29.22 PM.png>)

**ArgoCD Sync. Successfull**

![alt text](<project-pics/Screenshot 2024-04-12 at 1.38.43 PM.png>)

**Get the IP of the LB service type of the deployment**

![alt text](<project-pics/Screenshot 2024-04-12 at 1.36.12 PM.png>)

**Access the application**

![alt text](<project-pics/Screenshot 2024-04-12 at 1.36.41 PM.png>)

**Note the apllication tag**

![alt text](<project-pics/Screenshot 2024-04-12 at 1.37.57 PM.png>)

**CD Pipeline synced successfully after changing the tag**

![alt text](<project-pics/Screenshot 2024-04-12 at 1.38.43 PM.png>)

**Application tag changed**

![alt text](<project-pics/Screenshot 2024-04-12 at 1.39.22 PM.png>)

**Application Review**

![alt text](<project-pics/Screenshot 2024-04-12 at 1.40.50 PM.png>)

![alt text](<project-pics/Screenshot 2024-04-12 at 1.41.09 PM.png>)

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
