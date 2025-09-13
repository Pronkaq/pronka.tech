# pronka.tech

Учебный пет-проект для практики DevOps.  
Сайт-визитка + база данных PostgreSQL, завернутые в Docker и поднятые через docker-compose.

---

## 🔹 Что внутри
- 🌐 **Frontend** — простой сайт-визитка (HTML + CSS)  
- 🐳 **Dockerfile** — сборка образа сайта на базе `nginx:alpine`  
- 🗄️ **Database** — PostgreSQL 15 (с отдельным volume для хранения данных)  
- ⚙️ **docker-compose** — поднимает сайт и базу вместе одной командой  

---

## 🔹 Как запустить локально

Клонировать репозиторий:
```bash
git clone git@github.com:Pronkaq/pronka.tech.git
cd pronka.tech

СОбрать и поднять сервисы: 

docker-compose up -d --build

Проверить контейнеры:

docker-compose ls 

Сайт будет доступен по адресу: 

http://localhost:8080
