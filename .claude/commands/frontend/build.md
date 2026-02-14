---
description: Run frontend build with all quality checks
allowed-tools: Bash(npm run:*), Bash(cd:*)
---

Run complete frontend build verification:

```bash
# 1. Type checking
npm run lint

# 2. Format check
npm run format:check

# 3. Run tests
npm run test

# 4. Production build
npm run build
```

## On failure:
- For TypeScript errors: Show the exact error and suggest fixes
- For ESLint errors: Run `npm run lint:fix` if auto-fixable
- For Prettier errors: Run `npm run format` to fix
- For build errors: Analyze and suggest solutions

## Success criteria:
- All linting passes
- All formatting is correct
- All tests pass
- Build completes without errors
- dist/ directory is generated
