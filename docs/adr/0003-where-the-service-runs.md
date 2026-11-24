# 0003. Where the service runs

**Status / Статус:** Accepted

## Context / Контекст

We need one place where the service runs the same way for every team member and later in CI. / Нужно е едно място, където услугата работи еднакво за всички.

## Options / Варианти

- **Docker containers (locally/Codespaces, later a container platform)**: + same environment everywhere, fits Labs 3–8; − need to learn Docker.
- **Directly on a VM with Python installed**: + simple at first; − "works on my machine" problems, manual setup.

## Decision / Решение

The service runs in a Docker container, built from a Dockerfile in the repository. / Услугата работи в Docker контейнер.

## Consequences / Последствия

Every change needs a rebuilt image; the image becomes the artifact we deploy. / Всяка промяна изисква нов образ.
