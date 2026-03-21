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

#Build & push image
docker build -t kundanvrs/fastapi-app:latest .
docker push kundanvrs/fastapi-app:latest

#Create Helm chart
helm create fastapi-chart

#Deploy using Helm
helm install fastapi ./fastapi-chart

#Access app
minikube ip
kubectl get svc

👉 Open:

http://<minikube-ip>:30010

OR
minikube service fastapi
minikube service flask-service

#Upgrade
helm upgrade fastapi ./fastapi-chart

#Rollback
helm rollback fastapi 1