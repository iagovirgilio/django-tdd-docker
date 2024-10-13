# TDD DJANGO
Test Driven Development with Django

## DOCKER
### 1. Run this commands:
- Up
```bash
docker compose build
docker compose up -d
```
- Down
```bash
docker compose down -v
```

- Re-Build
```bash
docker compose up -d --build
```

### 2. Run the migrations:
```bash
docker compose exec movies python manage.py migrate --noinput
```

### 3. Check that the volume was created as well by running:
```bash
docker volume inspect django-tdd-docker_postgres_data
```