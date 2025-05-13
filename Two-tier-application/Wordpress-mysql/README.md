```markdown
**# 🐳 WordPress + MySQL on Kubernetes (Two-Tier Application)**

This project sets up a basic **two-tier application** using Kubernetes:
- ****WordPress**** for the frontend
- ****MySQL**** for the backend

All components are deployed inside a dedicated Kubernetes namespace.

---

## 📁 Project Structure

```

two-tier-wordpress/
├── namespace.yaml
├── mysql-deployment.yaml
├── mysql-service.yaml
├── wordpress-deployment.yaml
├── wordpress-service.yaml
└── README.md

````

---

## 🚀 Deployment Instructions

### 1. Create Namespace

```bash
kubectl apply -f namespace.yaml
````

### 2. Deploy MySQL (Backend)

```bash
kubectl apply -f mysql-deployment.yaml
kubectl apply -f mysql-service.yaml
```

### 3. Deploy WordPress (Frontend)

```bash
kubectl apply -f wordpress-deployment.yaml
kubectl apply -f wordpress-service.yaml
```

---

## 🌐 Access WordPress

* Access the WordPress frontend via your browser at:

```
http://<NODE_IP>:30080
```

* If using **Minikube**:

```bash
minikube service wordpress -n wordpress-app --url
```

---

## 🔐 Environment Variables

### MySQL

| Variable              | Value        |
| --------------------- | ------------ |
| `MYSQL_ROOT_PASSWORD` | `wordpress`  |
| `MYSQL_DATABASE`      | `wordpress`  |
| `MYSQL_USER`          | `wpuser`     |
| `MYSQL_PASSWORD`      | `wppassword` |

### WordPress

| Variable                | Value        |
| ----------------------- | ------------ |
| `WORDPRESS_DB_HOST`     | `mysql:3306` |
| `WORDPRESS_DB_USER`     | `wpuser`     |
| `WORDPRESS_DB_PASSWORD` | `wppassword` |
| `WORDPRESS_DB_NAME`     | `wordpress`  |

---

## 📌 Notes

* Storage is ephemeral (`emptyDir` used). For real-world use, replace with **Persistent Volumes**.
* MySQL and WordPress communicate via a ClusterIP service inside the namespace.

---

## 🧹 Clean Up

```bash
kubectl delete namespace wordpress-app
```

---
