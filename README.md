# Questionnaire App

## Описание
Это приложение включает Frontend и Backend сервисы, работающие в Kubernetes.

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
