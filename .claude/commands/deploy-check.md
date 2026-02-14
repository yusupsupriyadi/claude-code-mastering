---
description: Run all pre-deployment checks for all services
allowed-tools: Bash(docker compose:*), Bash(npm run:*), Bash(make:*), Bash(cd:*)
---

Run comprehensive pre-deployment checks for all services.

## Backend Checks
```bash
docker compose exec app uv run black app --check
docker compose exec app uv run ruff check app
docker compose exec app uv run mypy app
docker compose exec app uv run pytest app
make pre-deploy-check
```

## Frontend Checks
```bash
npm run lint
npm run format:check
npm run test
npm run build
```

## Additional Service Checks
For each additional service in the project:
```bash
npm run build  # or appropriate build command
docker build . # if applicable
```

## Success Criteria:
- [ ] Backend: All linting passes
- [ ] Backend: All tests pass
- [ ] Backend: Security checks pass
- [ ] Frontend: All linting passes
- [ ] Frontend: All tests pass
- [ ] Frontend: Build succeeds
- [ ] Additional services: Build succeeds
- [ ] Additional services: Docker builds (if applicable)

Report detailed results and block deployment if any check fails.
