# 0002. Database for Lab 4

**Status / Статус:** Accepted

## Context / Контекст

In Lab 4 notes must survive restarts, so the in-memory store is not enough. The app already supports PostgreSQL through `DATABASE_URL`. / В Упражнение 4 бележките трябва да оцеляват при рестарт.

## Options / Варианти

- **PostgreSQL**: + already supported by `PostgresNoteRepository`, official Docker image, industry standard; − one more container to run.
- **SQLite**: + a single file, no server; − not supported by the app, poor fit for several app replicas.

## Decision / Решение

We use PostgreSQL 16 in its own container, connected via `DATABASE_URL`. / Използваме PostgreSQL 16 в отделен контейнер.

## Consequences / Последствия

We need a volume for the data and a health check before the app starts. / Нужни са volume за данните и health check.
