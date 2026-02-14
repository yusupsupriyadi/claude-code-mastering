---
description: Run backend security checks before deployment
allowed-tools: Bash(make:*), Bash(docker compose exec:*)
---

Run comprehensive security checks for the backend.

Execute pre-deployment security check:
```
make pre-deploy-check
```

## Security checklist to verify:
1. No hardcoded secrets or credentials
2. All dependencies are up to date
3. SQL injection prevention (parameterized queries)
4. Authentication properly enforced
5. CORS configuration is correct
6. Input validation on all endpoints
7. Sensitive data properly encrypted

Report any security concerns found.
