# WordPress + MySQL on Kubernetes

This project deploys a two-tier application (WordPress + MySQL) using Kubernetes.

## 📁 Files

- `secret.yaml`: Stores MySQL credentials
- `mysql-deployment.yaml`: MySQL pod and volume
- `mysql-service.yaml`: Headless MySQL service
- `wordpress-deployment.yaml`: WordPress pod connected to MySQL
- `wordpress-service.yaml`: LoadBalancer service for WordPress

## 🧪 Steps to Deploy

1. Create secret:
```bash
kubectl apply -f secret.yaml
Deploy MySQL:

bash
Copy
Edit
kubectl apply -f mysql-deployment.yaml
kubectl apply -f mysql-service.yaml
Deploy WordPress:

bash
Copy
Edit
kubectl apply -f wordpress-deployment.yaml
kubectl apply -f wordpress-service.yaml
Access WordPress:

If you're using Minikube:

bash
Copy
Edit
minikube service wordpress
On Cloud: Check external IP from:

bash
Copy
Edit
kubectl get svc wordpress
🔒 Security Note
Secrets are encoded in base64, not encrypted.

Use Kubernetes Secret encryption in production.

