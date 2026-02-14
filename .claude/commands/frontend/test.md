---
description: Run frontend tests with Vitest
allowed-tools: Bash(npm run:*), Bash(cd:*)
argument-hint: "[test_pattern] (e.g., Button or --coverage)"
---

Run frontend tests using Vitest.

Test options: $ARGUMENTS

```bash
npm run test $ARGUMENTS
```

## Common usage:
- Run all tests: `/frontend/test`
- Run specific test: `/frontend/test Button`
- Run with coverage: `/frontend/test --coverage`
- Watch mode: `/frontend/test --watch`

## On test failures:
1. Show the failing test details
2. Analyze the expected vs actual output
3. Check the related component code
4. Suggest fixes for the failing tests
