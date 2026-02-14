# Deployment Rules

## Pre-deployment Checklist

Before any deployment, ensure all components can be built successfully.

### Frontend

- [ ] `npm run build` - Production build succeeds
- [ ] `npm run lint` - No linting errors
- [ ] `npm run format:check` - Formatting compliance
- [ ] `npm run test` - All tests pass
- [ ] Environment variables configured for production
- [ ] Build output in `dist/` generated successfully

### Backend

- [ ] `docker compose exec app uv run black app --check` - Code formatting
- [ ] `docker compose exec app uv run ruff check app` - No linting errors
- [ ] `docker compose exec app uv run mypy app` - Type checking passes
- [ ] `docker compose exec app uv run pytest app` - All tests pass
- [ ] `make pre-deploy-check` - Security compliance
- [ ] `docker compose build` - Docker image builds successfully
- [ ] `make migrate` - Database migrations tested and applied
- [ ] Environment variables set in appropriate `.env` files

### Additional Services

For each additional service in the project:

- [ ] Build/compile step succeeds
- [ ] Docker image builds successfully (if applicable)
- [ ] Dependencies installed
- [ ] Environment variables configured
- [ ] Service can connect to required external services

## Deployment Success Criteria

1. **Build Verification**: All build commands complete with exit code 0
2. **Test Coverage**: All existing tests pass
3. **Type Safety**: No TypeScript or Python type errors
4. **Code Quality**: All linting and formatting checks pass
5. **Docker Readiness**: All Docker images build successfully
6. **Environment Consistency**: Environment variables properly configured
7. **Database Integrity**: All migrations tested and reversible
8. **Service Health**: All microservices pass health checks

## Failure Recovery

If any build or deployment step fails:

1. **STOP** the deployment process immediately
2. **IDENTIFY** the root cause by checking logs and error messages
3. **FIX** the issue in the development environment first
4. **TEST** the fix thoroughly before attempting deployment again
5. **DOCUMENT** any configuration changes or fixes applied
