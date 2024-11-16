# Questionnaire App

## Описание
Этот проект представляет собой веб-приложение, состоящее из двух сервисов: Frontend (SPA) и Backend (API), развернутых в Kubernetes. 

## Развертывание

### Требования
- Kubernetes
- Docker
- Minikube (или другой кластер Kubernetes)

### Шаги
1. Примените манифесты:
   ```bash
   kubectl apply -f k8s-manifests/mongo.yaml
   kubectl apply -f k8s-manifests/backend.yaml
   kubectl apply -f k8s-manifests/frontend.yaml
   kubectl apply -f k8s-manifests/ingress.yaml
```markdown

