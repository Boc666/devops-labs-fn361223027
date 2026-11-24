# Service / Услугата

## Purpose / Предназначение

Notes API is a small HTTP service for creating and reading short text notes. It is the training app for the DevOps course: the app stays simple, and we build containers, a database, CI/CD and deployment around it. / Notes API е малка HTTP услуга за създаване и четене на кратки бележки. Тя е учебното приложение в курса по DevOps: самото приложение е просто, а около него изграждаме контейнери, база данни, CI/CD и внедряване.

## Endpoints / Адреси

| Method | Path | What it does / Какво прави |
|---|---|---|
| GET | /health | Liveness check, returns `{"status": "ok"}`. / Проверка дали услугата е жива. |
| GET | /ready | Readiness check: pings the storage; `{"status": "ready"}` or 503 `{"status": "storage unavailable"}`. / Проверява дали хранилището на данни отговаря; иначе 503. |
| GET | /version | Returns `{"version": ...}` from `APP_VERSION` (default `0.1.0`). / Версията от `APP_VERSION`. |
| GET | /model | Which ML model file is loaded (`MODEL_PATH`), or `null`. / Кой ML модел е зареден, или `null`. |
| GET | /notes | Lists all notes. / Списък с всички бележки. |
| POST | /notes | Creates a note from JSON `{"title", "body"}`; `title` is 1–100 characters; returns 201. / Създава бележка; `title` е 1–100 знака; връща 201. |
| GET | /notes/{id} | One note by id; 404 `Note not found` if missing. / Една бележка; 404, ако я няма. |

## Dependencies / Зависимости

- Python 3.12 and the packages in `requirements.txt` (FastAPI, Uvicorn, psycopg). / Python 3.12 и пакетите от `requirements.txt`.
- Optional PostgreSQL via `DATABASE_URL`; without it notes are kept in memory and lost on restart. / По желание PostgreSQL чрез `DATABASE_URL`; без него бележките са в паметта.
- Optional ML model via `MODEL_PATH` (Lab 10). / По желание ML модел чрез `MODEL_PATH`.
