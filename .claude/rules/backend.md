# Backend Development Rules

## Testing and Script Execution

- **ALWAYS** run backend tests and scripts through Docker Compose containers
- Use `docker compose exec` or similar commands to execute code within the containerized environment
- **NEVER** run backend Python code directly on the host system
- Ensure all dependencies and environment variables are properly configured within containers

## Code Quality Commands

```bash
# Format check
docker compose exec app uv run black app --check

# Linting
docker compose exec app uv run ruff check app

# Type checking
docker compose exec app uv run mypy app

# Run tests
docker compose exec app uv run pytest app
```

## Database Migrations

- Use `make migrate` to run database migrations
- Use `make makemigrations` to create new migration files
- Always check migration files before applying them
- Ensure migrations are tested in the development environment first
- When editing migration files, use `make makemigrations` command

## Development Workflow

- Verify that Docker Compose services are running before executing backend operations
- Check container logs for errors when debugging backend issues
- Use appropriate container networking when connecting services

## Integration Development

- When developing new integrations, refer to existing integration implementations
- Follow the established patterns for OAuth authentication, API calls, and data handling
- Ensure proper error handling and user feedback mechanisms
