 WordPress on Kubernetes Deployment

A complete WordPress + MySQL deployment on Kubernetes with horizontal scaling and service discovery.

📋 Overview

This project demonstrates a production-ready WordPress deployment on Kubernetes featuring:
- WordPress with horizontal scaling (3 replicas)
- MySQL database with persistent storage  
- Service discovery and load balancing
- External access via NodePort (30081)

🏗️ Architecture

KUBERNETES CLUSTER
==================

Load Balancer (NodePort:30081)
↓
WordPress Service (ClusterIP:80)
↓
WordPress Deployment (3 Replicas)
↓
MySQL Service (ClusterIP:3306)
↓
MySQL Deployment (1 Replica + PVC)


Quick Start

```bash
# Deploy everything
kubectl apply -f manifests/

# Verify deployment
kubectl get all

# Access WordPress
# http://<worker-node-ip>:30081

📁 Project Structure
text
kubernetes-wordpress-deployment/
└── manifests/
    ├── mysql.yaml          # MySQL service & deployment
    ├── wordpress.yaml      # WordPress service & deployment  
    └── mysql-pvc.yaml      # Persistent volume claim


**# Scale WordPress**
kubectl scale deployment wordpress --replicas=5

**# Check logs**
kubectl logs -l app=wordpress

**# Delete deployment**
kubectl delete -f manifests/

**📝 Learnings**

This project demonstrates:

Kubernetes Deployments & Services

Horizontal scaling concepts

Service discovery & networking

Persistent Volume Claims

Multi-container architecture



