# 🌐 Pronka.tech — DevOps Pet Project

Учебный pet-project для практики CI/CD и контейнеризации.  
Задача: развернуть простой сайт-визитку и автоматизировать его деплой.

---

## 🚀 Стек технологий
- **Docker** — контейнеризация приложения
- **Docker Compose** — описание и запуск сервисов
- **GitHub Actions** — CI/CD пайплайны
- **DockerHub** — хранение образов
- **Yandex Cloud (Ubuntu 22.04)** — сервер для продакшна
- **nginx:alpine** — веб-сервер для статики

---

## ⚙️ Архитектура проекта
1. **Frontend** (статический сайт) → обёрнут в Docker (`nginx:alpine`).
2. **Docker Compose** в продакшне:
   ```yaml
   services:
     web:
       image: pronkaq/pronka-site:latest
       restart: unless-stopped
       ports:
         - "80:80"

    CI/CD:

        Build → GitHub Actions собирает образ и пушит в DockerHub.

        Deploy → GitHub Actions по SSH заходит на сервер и обновляет контейнер.

        Автоматический рестарт при каждом пуше в main.

🔄 CI/CD Workflow

.github/workflows/dockerhub.yml:

    Build job

        checkout репозитория

        login в DockerHub

        build & push Docker image

    Deploy job

        подключение по SSH (appleboy/ssh-action)

        docker compose pull && docker compose up -d

        очистка старых образов (docker image prune -f)

🖥️ Как работает деплой

    Разработчик пушит изменения в ветку main.

    GitHub Actions автоматически:

     собирает образ → пушит в DockerHub

     заходит на сервер → обновляет контейнер

    Через несколько секунд сайт доступен по IP/домену.

✅ Что я прокачал

    Настройка SSH и управление ключами

    Работа с Docker и Compose в dev/prod среде

    Настройка GitHub Actions (jobs, needs, secrets)

    Автоматизация деплоя на VPS

    CI/CD как у «настоящего» проекта

📝 ToDo (план развития)

Подключить HTTPS (Caddy или Nginx + Let’s Encrypt)

Добавить staging-окружение (отдельный compose на порту 8081)

Настроить мониторинг (Prometheus + Grafana)

Добавить линтер Dockerfile в CI (hadolint)


