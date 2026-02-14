---
description: Create or run database migrations
allowed-tools: Bash(make:*), Bash(docker compose exec:*)
argument-hint: "[action: create|run|status] [message for create]"
---

Manage database migrations for the backend.

Action: $ARGUMENTS

## Available actions:

### Create new migration
If action is "create" with a message:
```
make makemigrations
```
Then review the generated migration file in `alembic/versions/`

### Run migrations
If action is "run" or empty:
```
make migrate
```

### Check migration status
If action is "status":
```
docker compose exec app uv run alembic current
docker compose exec app uv run alembic history --verbose
```

## Best practices:
- Always review migration files before applying
- Ensure migrations are reversible (downgrade path)
- Test in development before production
- Consider data migration for schema changes
