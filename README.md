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

Клонируйте репозиторий с помощью команды: `git clone https://github.com/KrupskiiAndrei/questionnaire-app.git && cd questionnaire-app`. Убедитесь, что у вас установлен Minikube. Запустите Minikube с помощью команды `minikube start`, если он еще не запущен. Проверьте IP-адрес Minikube командой `minikube ip`. Допустим, он равен `192.168.49.2`. Добавьте следующую строку в файл `/etc/hosts`: `192.168.49.2  questionnaire.local`. Сохраните файл, чтобы иметь возможность обращаться к приложению по домену `http://questionnaire.local`.

Примените все манифесты для развертывания приложения в Kubernetes с помощью команды: `kubectl apply -f k8s-manifests/`. Проверьте, что все Pods находятся в состоянии Running, выполнив команду `kubectl get pods`. Вы должны увидеть, что все Pods находятся в статусе `Running`. Например: `mongo-6b86d46dfc-8xk4p 1/1 Running 0 3m`, `questionnaire-backend-6b79fd697b-kvff9 1/1 Running 0 2m`, `questionnaire-frontend-5cfbff95dc-78x6z 1/1 Running 0 1m`.

Также проверьте, что сервисы запущены корректно с помощью команды `kubectl get services` и что Ingress настроен правильно с помощью команды `kubectl get ingress`. Убедитесь, что для Ingress настроен домен `questionnaire.local` и адрес соответствует IP Minikube.

Откройте браузер и перейдите по адресу `http://questionnaire.local`. На главной странице создайте новый опрос, введя вопрос и варианты ответов. Проверьте, что опрос успешно создается. Затем откройте несколько экземпляров браузера в режиме инкогнито и проверьте синхронизацию данных между клиентами через WebSocket. Убедитесь, что данные сохраняются корректно в MongoDB.

Если возникают ошибки, проверьте логи Pod-ов с помощью команды `kubectl logs <pod-name>`. После завершения проверки удалите все созданные ресурсы с помощью команды `kubectl delete -f k8s-manifests/`.

Структура проекта включает следующие папки и файлы: `backend/` — исходный код и Dockerfile для Backend, `frontend/` — исходный код и Dockerfile для Frontend, `k8s-manifests/` — манифесты Kubernetes для развертывания приложения. В папке `k8s-manifests/` находятся следующие манифесты: `mongo.yaml` — для MongoDB, `backend.yaml` — для Backend, `frontend.yaml` — для Frontend, `ingress.yaml` — для Ingress.

Приложение использует следующие технологии: Frontend написан на TypeScript с использованием Angular, Backend — на TypeScript с использованием Express, MongoDB и Socket.IO. Для деплоя используются Kubernetes, Docker и Minikube.
