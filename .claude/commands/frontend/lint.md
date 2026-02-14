---
description: Run frontend linting and formatting
allowed-tools: Bash(npm run:*), Bash(cd:*)
argument-hint: "[--fix to auto-fix issues]"
---

Run frontend code quality checks.

Options: $ARGUMENTS

## Check mode (default):
```bash
npm run lint
npm run format:check
```

## Fix mode (if --fix provided):
```bash
npm run lint:fix
npm run format
```

Report all issues found and provide specific fixes for any that cannot be auto-corrected.
