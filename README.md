# 🚀 Kubernetes Cluster Deployment & Microservices Architecture

Built with Kubernetes, Docker, React.js, Node.js, MongoDB, Prometheus, Grafana, and AWS EC2

### 



## 📌 Project Overview

This project demonstrates the deployment of a complete Microservices Architecture on a Kubernetes Cluster using Minikube. The application consists of multiple independent services communicating through Kubernetes networking and managed using Deployments, Services, Ingress, Horizontal Pod Autoscaling, Rolling Updates, and Self-Healing mechanisms.

The project simulates a production-like cloud-native environment and showcases Kubernetes orchestration capabilities such as container orchestration, service discovery, load balancing, rolling updates, horizontal scaling, self-healing, monitoring, and observability.

---

## 🏗️ Architecture

```text
                    User
                      |
                      ▼
                 Ingress Controller
                      |
    -----------------------------------------
    |                |                     |
    ▼                ▼                     ▼
 Frontend       User Service         Product Service
                                       |
                                       ▼
                                  Order Service
                                       |
                                       ▼
                                    MongoDB
```

---

## ⚙️ Technologies Used

- Kubernetes
- Docker
- Minikube
- Node.js
- MongoDB
- Prometheus
- Grafana
- Git & GitHub
- Ubuntu Linux
- AWS EC2

---

## 📂 Project Structure

```text
Kubernetes-Microservices-Project/
│
├── app/
│   ├── frontend/
│   ├── user-service/
│   ├── product-service/
│   └── order-service/
│
├── k8s-manifests/
│   ├── frontend-deployment.yaml
│   ├── frontend-service.yaml
│   ├── user-deployment.yaml
│   ├── user-service.yaml
│   ├── product-deployment.yaml
│   ├── product-service.yaml
│   ├── order-deployment.yaml
│   ├── order-service.yaml
│   ├── mongodb-deployment.yaml
│   ├── mongodb-service.yaml
│   └── ingress.yaml
│
├── screenshots/
│
└── README.md
```

---

## 🚀 Features

✅ Multi-Service Application Deployment

✅ Kubernetes Deployments & Services

✅ MongoDB Integration

✅ Ingress Controller Configuration

✅ Horizontal Pod Autoscaler (HPA)

✅ Rolling Updates

✅ Self-Healing Demonstration

✅ Prometheus Monitoring

✅ Grafana Dashboard Visualization

✅ Production-Like Kubernetes Environment

---

## 🔧 Prerequisites

Before starting, ensure the following tools are installed:

- Docker
- Kubernetes
- Minikube
- kubectl
- Git
- Node.js
- AWS EC2 Instance

---

## 🚀 Deployment Steps

### Step 1: Clone Repository

```bash
git clone https://github.com/<your-github-username>/Kubernetes-Microservices-Project.git

cd Kubernetes-Microservices-Project
```

### Step 2: Start Minikube Cluster

```bash
minikube start --driver=docker --cpus=4 --memory=8192
```

Verify Cluster:

```bash
kubectl get nodes
```

---

### Step 3: Create Namespace

```bash
kubectl create namespace microservices
```

Verify:

```bash
kubectl get ns
```

---

### Step 4: Build Docker Images

Frontend

```bash
docker build -t frontend:v1 .
```

User Service

```bash
docker build -t user-service:v1 .
```

Product Service

```bash
docker build -t product-service:v1 .
```

Order Service

```bash
docker build -t order-service:v1 .
```

---

### Step 5: Load Images into Minikube

```bash
minikube image load frontend:v1

minikube image load user-service:v1

minikube image load product-service:v1

minikube image load order-service:v1
```

---

### Step 6: Deploy Kubernetes Resources

```bash
kubectl apply -f k8s-manifests/
```

Verify:

```bash
kubectl get all -n microservices
```

---

## 🌐 Ingress Configuration

Enable Ingress Controller:

```bash
minikube addons enable ingress
```

Verify:

```bash
kubectl get ingress -n microservices
```

---

## 📈 Horizontal Pod Autoscaler (HPA)

Enable Metrics Server:

```bash
minikube addons enable metrics-server
```

Create HPA:

```bash
kubectl autoscale deployment frontend \
--cpu-percent=50 \
--min=1 \
--max=5 \
-n microservices
```

Verify:

```bash
kubectl get hpa -n microservices
```

---

## 🔄 Rolling Updates

Deploy New Application Version:

```bash
kubectl set image deployment/frontend frontend=frontend:v2 -n microservices
```

Monitor Update:

```bash
kubectl rollout status deployment/frontend -n microservices
```

Verify Replica Sets:

```bash
kubectl get rs -n microservices
```

---

## 🛡️ Self-Healing Demonstration

Delete Running Pod:

```bash
kubectl delete pod <pod-name> -n microservices
```

Watch Kubernetes Automatically Recreate Pod:

```bash
kubectl get pods -n microservices -w
```

---

## 📊 Monitoring with Prometheus

Install Prometheus:

```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts

helm repo update

helm install prometheus prometheus-community/prometheus
```

Access Prometheus:

```text
http://<EC2-PUBLIC-IP>:9090
```

Useful Prometheus Query:

```text
up
```

---

## 📉 Grafana Dashboard

Run Grafana:

```bash
docker run -d \
-p 3000:3000 \
--name grafana \
grafana/grafana
```

Access Grafana:

```text
http://<EC2-PUBLIC-IP>:3000
```

Default Login:

```text
Username: admin
Password: admin
```

Configure Prometheus Data Source:

```text
http://<PROMETHEUS-IP>:9090
```

---

## 📸 Project Screenshots

### Kubernetes Cluster


AWS EC2 Instance

<img width="1920" height="1025" alt="running instance" src="https://github.com/user-attachments/assets/73c44843-153f-4b4c-9ff8-ab37ac59e497" />

Minikube Running

<img width="1920" height="1080" alt="minikube-running png" src="https://github.com/user-attachments/assets/a2204a45-f5aa-4754-8f2d-e3069eaa9355" />

Docker Images
<img width="1920" height="1080" alt="docker images" src="https://github.com/user-attachments/assets/16af101f-5f20-4377-b177-3189c6fe2d36" />

Kubernetes Node
<img width="1920" height="561" alt="kubernetes-node png" src="https://github.com/user-attachments/assets/032a8ac5-f3d9-4f88-97e0-90588ddb08ab" />

Running Pods

<img width="1920" height="561" alt="running-pods png" src="https://github.com/user-attachments/assets/7c80b16d-fbcb-4379-8813-da45392b36d8" />

Kubernetes Services

<img width="1920" height="561" alt="kubernetes-services png" src="https://github.com/user-attachments/assets/3ddc5ae9-dc28-4910-a606-de83c6b6225a" />

Ingress

<img width="1920" height="561" alt="ingress png" src="https://github.com/user-attachments/assets/9d9796df-bdb1-48cd-b319-7737b91f7931" />

React Frontend

<img width="1920" height="1023" alt="react-frontend png" src="https://github.com/user-attachments/assets/65489b74-2e06-4fa6-a4a3-95d29d88c8e3" />

User API

<img width="1920" height="561" alt="user-api png" src="https://github.com/user-attachments/assets/ad81055a-a329-4d8f-8924-9ccba697f0c0" />

Product API

<img width="1920" height="561" alt="product-api png" src="https://github.com/user-attachments/assets/e0447d80-37c8-4035-ae70-8904850d1cfb" />

Order API

<img width="1920" height="561" alt="order-api png" src="https://github.com/user-attachments/assets/a0c2dfa1-5b4e-4a08-be59-59e6d82326dd" />

Rolling Update

<img width="1920" height="561" alt="rolling-update png" src="https://github.com/user-attachments/assets/0e4d07bf-bfab-41d3-90e3-9fcb69b33957" />

Horizontal Pod Autoscaler

<img width="636" height="382" alt="image" src="https://github.com/user-attachments/assets/e7f246f5-7873-424b-b36c-94fc1dbae6e1" />

Self-Healing

<img width="1920" height="599" alt="self-healing png" src="https://github.com/user-attachments/assets/a47af14e-9fd3-4e74-a488-71d5ca121a46" />

Final Output


<img width="336" height="330" alt="image" src="https://github.com/user-attachments/assets/faac52de-925e-4b0e-9ab1-dce0ebc78f2d" />

****


### Application Screenshots

- Frontend Application
- User API
- Product API
- Order API
- MongoDB Running

### Kubernetes Features

- Ingress Configuration
- Horizontal Pod Autoscaler
- Rolling Update
- Self-Healing

### Monitoring

- Prometheus Home
- Prometheus Targets
- Prometheus Metrics
- Grafana Dashboard

---

## 🎯 Learning Outcomes

Through this project, I gained hands-on experience with:

- Kubernetes Cluster Setup
- Microservices Architecture
- Container Orchestration
- Kubernetes Networking
- Deployments & Services
- Ingress Controller
- Auto Scaling
- Rolling Updates
- Self-Healing Mechanism
- Prometheus Monitoring
- Grafana Visualization
- Production-Level DevOps Practices

---

## 👨‍💻 Author

### Ashu Chamle

Cloud & DevOps Engineer

Skills:
- AWS
- Docker
- Kubernetes
- Terraform
- Jenkins
- Linux
- GitHub Actions
- Prometheus
- Grafana

---
