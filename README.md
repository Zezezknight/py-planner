# Студенческий планировщик

> **Студенческий планировщик** — это веб-приложение, созданное для управления пользовательскими задачами и импорта задач из сторонних сервисов

---


## 🛠 Технологии

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)

---

## ✨ Основной функционал

* **CRUD задачи:** Создание, обновление, удаление задач
* **Авторизация:** Безопасная аутентификация пользователей с использованием JWT-токенов
* **Импорт из внешних API:**
  * ☀️ **Open-Meteo:** Автоматический импорт погодных предупреждений (жара/холод)
  * 🚀 **Spaceflight News:** Импорт новостей освоения космоса
  * 🌐 **Nager.Date:** Импорт публичных и праздничных дней
* **Кэширование:** Ускорение работы с частыми запросами через Redis

---

## 🚀 Быстрый старт

**Требования к окружению:**

* Docker и Docker Compose
* Python 3.11+ (при локальной разработке без Docker)

Клонируйте репозиторий и запустите проект через Docker:

```bash
# Клонирование репозитория
git clone git@github.com:Zezezknight/py-planner.git
cd ./py-planner

# Настройка переменных окружения
cp .env.example .env

# Запуск контейнеров
docker compose up -d
```

---

### 🔗 Полезные ссылки (Локально)

- 📖 **API Документация (Swagger):** [http://localhost:8000/docs](http://localhost:8000/docs)

---

## ⚙️ Переменные окружения (.env)

```.env
# ============================================
# ENVIRONMENT CONFIGURATION TEMPLATE (.env.example)
# Copy to .env and configure for your needs
# ============================================

# === DATABASE ===
MONGO_URI=mongodb://root:example@mongo:27017
MONGO_DB_NAME=planner
MONGO_POOL_SIZE=10

# === AUTHENTICATION & JWT ===
JWT_SECRET=dev-secret-change-me-32-characters-minimum
JWT_ALG=HS256
JWT_EXPIRE_MINUTES=60

# === APPLICATION ===
APP_NAME=studplanner
APP_ENV=dev

# === HTTP & NETWORK ===
HTTP_TIMEOUT=10
HTTP_MAX_CONNECTIONS=10

# === REDIS & CACHING ===
REDIS_URL=redis://redis:6379/0
REDIS_POOL_SIZE=10

CACHE_ENABLED=true
CACHE_TTL_TASKS=900
CACHE_TTL_SECONDS=900
CACHE_MAX_BYTES=1048576
CACHE_TTL_PREVIEW=300

# === LOGGING ===
LOG_LEVEL=INFO
LOG_FORMAT=json
LOG_FILE_PATH=logs/app.log
LOG_ROTATE_MB=10
LOG_BACKUP_COUNT=5

# === BACKGROUND TASKS & SCHEDULER ===
SCHEDULER_ENABLED=true

# Auto import
AUTO_IMPORT_ENABLED=false
AUTO_IMPORT_INTERVAL_MINUTES=60

# Data cleanup
CLEANUP_ENABLED=true
CLEANUP_INTERVAL_HOURS=24
CLEANUP_EXPIRED_DAYS=90

# Reminders
REMINDERS_ENABLED=true
REMINDER_CHECK_INTERVAL_MINUTES=15
REMINDER_BEFORE_MINUTES=30
```

---

## 📂 Структура репозитория

```text
.
├── src/
│   ├── app/
│   │   ├── api/            # Эндпоинты, роуты и валидация запросов
│   │   ├── cache/          # Клиент и логика работы с Redis
│   │   ├── core/           # Конфигурация приложения, безопасность
│   │   ├── db/             # Репозитории
│   │   ├── external/       # Клиенты для внешних сервисов
│   │   ├── middleware/     # Middleware для FastAPI
│   │   ├── models/         # Схемы Pydantic и модели данных
│   │   ├── services/       # Бизнес-логика приложения
│   │   ├── __init__.py
│   │   └── main.py         # Точка входа в приложение FastAPI
│   └── __init__.py
├── .env.example            # Шаблон переменных окружения
├── .gitignore
├── docker-compose.yaml     # Оркестрация контейнеров (FastAPI, MongoDB, Redis)
├── Dockerfile              # Сборка образа приложения
├── LICENSE
├── Makefile                # Команды для быстрой сборки, запуска и тестирования
├── README.md               # Документация проекта
└── requirements.txt        # Зависимости проекта

```
