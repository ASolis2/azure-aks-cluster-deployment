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

