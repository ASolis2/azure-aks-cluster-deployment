# Azure AKS Cluster Deployment

This project demonstrates how to deploy a basic Kubernetes cluster (AKS) on Microsoft Azure, deploy an Nginx web application, expose it to the internet using a LoadBalancer, and clean up resources afterward.

## Project Summary

- **Cloud Platform**: Microsoft Azure
- **Orchestration**: Kubernetes (AKS)
- **Tools Used**: Azure CLI, kubectl, WSL2 (Ubuntu)
- **App Deployed**: Nginx Web Server

---

## Project Steps

### 1. Create Resource Group
```bash
az group create --name aks-resource-group --location centralus
```

### 2. Create AKS Cluster
```bash
az aks create --resource-group aks-resource-group --name aks-cluster --node-count 1 --enable-addons monitoring --generate-ssh-keys --node-vm-size Standard_B2s
```

### 3. Install kubectl and Connect to Cluster
```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
mkdir -p ~/bin
mv kubectl ~/bin/kubectl
export PATH=$PATH:$HOME/bin
source ~/.bashrc
kubectl version --client
```

### 4. Connect to AKS Cluster
```bash
az aks get-credentials --resource-group aks-resource-group --name aks-cluster
```

### 5. Deploy Nginx to the Cluster
```bash
kubectl create deployment nginx-deployment --image=nginx
kubectl get deployments
kubectl get pods
```

### 6. Expose Nginx Deployment
```bash
kubectl expose deployment nginx-deployment --port=80 --type=LoadBalancer
kubectl get services
```

### 7. Clean Up Resources
```bash
az group delete --name aks-resource-group --yes --no-wait
az group list
```

---

## Screenshots

| Step | Screenshot |
|:---|:---|
| AKS Cluster Created (Part 1) | ![](./screenshots/aks-cluster-created-1.png) |
| AKS Cluster Created (Part 2) | ![](./screenshots/aks-cluster-created-2.png) |
| AKS Cluster Created (Part 3) | ![](./screenshots/aks-cluster-created-3.png) |
| AKS Cluster Created (Part 4) | ![](./screenshots/aks-cluster-created-4.png) |
| Connected to Cluster | ![](./screenshots/aks-connected.png) |
| kubectl Installed | ![](./screenshots/kubectl-installed.png) |
| Nginx Deployment Created | ![](./screenshots/nginx-deployment-created.png) |
| Get Deployments Output | ![](./screenshots/nginx-get-deployments.png) |
| Get Pods Output | ![](./screenshots/nginx-get-pods.png) |
| Get Services Output | ![](./screenshots/nginx-get-services.png) |
| Nginx Service Exposed | ![](./screenshots/nginx-service-exposed.png) |
| Resource Group Deleted (Command) | ![](./screenshots/aks-resource-group-delete-command.png) |
| Resource Group Deleted (Confirmation 1) | ![](./screenshots/aks-resource-group-deleted-1.png) |
| Resource Group Deleted (Confirmation 2) | ![](./screenshots/aks-resource-group-deleted-2.png) |

---

## Future Improvements

- Automate entire AKS deployment with a single Bash script
- Expand deployment with custom Docker containers
- Add ingress controller for advanced routing

---

## Author

- **Anthony Solis** — [GitHub Profile](https://github.com/ASolis2)

---



