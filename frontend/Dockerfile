# Используем официальный образ nginx для Frontend
FROM nginx:latest

# Удаляем стандартный index.html nginx
RUN rm -rf /usr/share/nginx/html/*

# Копируем собранные файлы Frontend в nginx
COPY dist/questionnaire-frontend /usr/share/nginx/html

# Копируем кастомный файл конфигурации nginx
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Указываем порт для работы nginx
EXPOSE 80

# Старт nginx
CMD ["nginx", "-g", "daemon off;"]
