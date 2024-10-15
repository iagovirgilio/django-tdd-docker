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
docker compose down
```
- Down (remove volume)
```bash
docker compose down -v
```

- Re-Build
```bash
docker compose up -d --build
```doc

### 2. Run the migrations:
```bash
docker compose exec movies python manage.py migrate --noinput
```

### 3. Check that the volume was created as well by running:
```bash
docker volume inspect django-tdd-docker_postgres_data
```

### 4. Seed database
```bash
docker compose exec movies python manage.py flush
docker compose exec movies python manage.py loaddata movies.json
```

### 5. Generate SECRET_KEY
```bash
docker compose exec movies python -c "from django.core.management.utils import get_random_secret_key; print(get_random_secret_key())"
```

## HTTPie
### Test insert
```bash
http --json POST http://localhost:8009/api/movies/ title=Fargo genre=comedy year=1996
```
### Get all movies
```bash
http --json http://localhost:8009/api/movies/
```
### Get single movie
```
http --json http://localhost:8009/api/movies/1/ 
```

## Pytest Commands

- Normal run
    ```bash
    docker compose exec movies pytest
    ```

- Disable warnings
    ```bash
    docker compose exec movies pytest -p no:warnings
    ```

- Run only the last failed tests
    ```bash
    docker compose exec movies pytest --lf
    ```

- Run only the tests with names that match the string expression
    ```bash
    docker compose exec movies pytest -k "movie and not all_movies"
    ```

- Stop the test session after the first failure
    ```bash
    docker compose exec movies pytest -x
    ```

- Enter PDB after first failure then end the test session
    ```bash
    docker compose exec movies pytest -x --pdb
    ```

- Stop the test run after two failures
    ```bash
    docker compose exec movies pytest --maxfail=2
    ```

- Show local variables in tracebacks
    ```bash
    docker compose exec movies pytest -l
    ```

- list the 2 slowest tests
    ```bash
    docker compose exec movies pytest --durations=2
    ```
