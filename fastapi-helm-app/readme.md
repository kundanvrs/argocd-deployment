
## 📦 Project Structure

```

fastapi-helm-app/
├── app/                     # FastAPI application code
│   ├── app.py
│   └── requirements.txt
│
├── Dockerfile              # Container build file
│
├── helm/                   # Helm chart
│   └── fastapi-chart/
│       ├── Chart.yaml
│       ├── values.yaml
│       ├── values-dev.yaml
│       ├── values-qa.yaml
│       ├── values-prod.yaml
│       └── templates/
│           ├── deployment.yaml
│           ├── service.yaml
│           └── ingress.yaml   # optional (prod)
│
└── README.md

````

---

## ⚙️ Prerequisites

- Kubernetes (Minikube or cluster)
- Docker
- Helm
- kubectl

---

## 🐳 Build & Push Docker Image

```bash
docker build -t kundanvrs/fastapi-app:latest .
docker push kundanvrs/fastapi-app:latest
````

---

## 📦 Create Helm Chart

```bash
helm create fastapi-chart
```

> Move or replace this chart inside `helm/fastapi-chart/`

---

## 🚀 Deploy using Helm

```bash
helm install fastapi ./helm/fastapi-chart
```

---

## 🌐 Access Application

### Option 1: Using Minikube IP

```bash
minikube ip
kubectl get svc
```

Open in browser:

```
http://<minikube-ip>:30010
```

---

### Option 2: Using Minikube Service (Recommended)

```bash
minikube service fastapi
```

---

## 🔄 Upgrade Application

```bash
helm upgrade fastapi ./helm/fastapi-chart
```

---

## ⏪ Rollback Deployment

```bash
helm rollback fastapi 1
```

---

## ⚙️ Environment Configurations

Use different values files:

```bash
# Dev
helm install fastapi ./helm/fastapi-chart -f values-dev.yaml

# QA
helm install fastapi ./helm/fastapi-chart -f values-qa.yaml

# Prod
helm install fastapi ./helm/fastapi-chart -f values-prod.yaml
```

---
