---
description: Run all backend code quality checks
allowed-tools: Bash(docker compose exec:*)
argument-hint: "[--fix to auto-fix issues]"
---

Run backend code quality checks (black, ruff, mypy).

Options: $ARGUMENTS

## Check mode (default):
```
docker compose exec app uv run black app --check
docker compose exec app uv run ruff check app
docker compose exec app uv run mypy app
```

## Fix mode (if --fix provided):
```
docker compose exec app uv run black app
docker compose exec app uv run ruff check app --fix
```

Report all issues found and suggest fixes for any that cannot be auto-corrected.
