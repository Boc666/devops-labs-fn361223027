# Runbook

## Start locally / Локално стартиране

```bash
python3.12 -m venv .venv
source .venv/bin/activate
pip install -r requirements-dev.txt
uvicorn app.main:app --reload --port 9000
```

## Check that it works / Проверка, че работи

```bash
curl -s http://127.0.0.1:9000/health    # {"status":"ok"}
curl -s http://127.0.0.1:9000/ready     # {"status":"ready"}
curl -s http://127.0.0.1:9000/version   # {"version":"0.1.0"}
```

Interactive API docs: open http://127.0.0.1:9000/docs. / Документация на API: http://127.0.0.1:9000/docs.

## Run the tests / Тестове

```bash
pytest
ruff check .
```

## When something breaks / Когато нещо се счупи

1. Is the process running and listening on the port? / Работи ли процесът и слуша ли на порта?
   `curl -s http://127.0.0.1:9000/health` and check the terminal where `uvicorn` runs for a traceback.
2. Can it reach its storage? / Достига ли базата?
   `curl -s -i http://127.0.0.1:9000/ready` — 503 means check `DATABASE_URL` and that PostgreSQL is up.
3. Did a recent change break it? / Счупи ли го последна промяна?
   `git log --oneline -5`, then `pytest` to find the failing part.
