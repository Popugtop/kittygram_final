# Kittygram

Веб-приложение для публикации фотографий котиков. Пользователи могут регистрироваться, добавлять своих котов с фотографиями, указывать имя, год рождения и цвет.

## Стек технологий

- Python 3.9
- Django 3.2
- Django REST Framework
- PostgreSQL 13
- Nginx
- Docker / Docker Compose
- GitHub Actions

## Развёртывание проекта

### 1. Клонировать репозиторий

```bash
git clone https://github.com/your-username/kittygram_final.git
cd kittygram_final
```

### 2. Создать файл .env

Скопируйте пример и заполните значения:

```bash
cp .env.example .env
```

Содержимое `.env`:

```
SECRET_KEY=ваш-секретный-ключ-django
DEBUG=False
ALLOWED_HOSTS=localhost 127.0.0.1

POSTGRES_DB=kittygram
POSTGRES_USER=kittygram_user
POSTGRES_PASSWORD=ваш-пароль
DB_HOST=db
DB_PORT=5432
```

### 3. Запустить контейнеры

```bash
docker compose up -d
```

Проект будет доступен по адресу: http://localhost:9000

## Структура проекта

```
kittygram_final/
├── backend/        # Django-бэкенд
├── frontend/       # React-фронтенд
├── nginx/          # Конфигурация gateway
├── docker-compose.yml
└── .env.example
```

## CI/CD

При пуше в ветку `main` автоматически:
1. Запускаются тесты (ruff + pytest)
2. Собираются и загружаются образы на Docker Hub
3. Приходит уведомление в Telegram

Для работы CI/CD нужно добавить секреты в GitHub репозиторий:
- `DOCKER_USERNAME` — логин на Docker Hub
- `DOCKER_PASSWORD` — пароль на Docker Hub
- `TELEGRAM_TO` — ID чата в Telegram
- `TELEGRAM_TOKEN` — токен Telegram-бота
