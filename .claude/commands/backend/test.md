---
description: Run backend pytest tests via Docker Compose
allowed-tools: Bash(docker compose exec:*)
argument-hint: "[test_path] (e.g., app/tests/test_users.py or app/tests/ -k 'test_create')"
---

Run backend tests using Docker Compose.

Test target: $ARGUMENTS

Execute the following command:
```
docker compose exec app uv run pytest $ARGUMENTS -v
```

If tests fail:
1. Analyze the failure output
2. Identify the root cause
3. Suggest specific fixes with code examples

If no arguments provided, run all tests:
```
docker compose exec app uv run pytest app -v
```
