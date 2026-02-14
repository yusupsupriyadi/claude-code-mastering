---
description: Run Terraform plan for infrastructure changes
allowed-tools: Bash(make:*), Bash(cd:*)
argument-hint: "[environment: dev|stg|prod]"
---

Run Terraform plan to preview infrastructure changes.

Environment: $1

## Execute:
```bash
make plan-$1
```

## Environment mapping:
- `dev` - Development environment (AWS_PROFILE=your-dev-profile)
- `stg` - Staging environment
- `prod` - Production environment (AWS_PROFILE=your-prod-profile)

## After running:
1. Analyze the plan output
2. Identify resources to be created/modified/destroyed
3. Highlight any potentially destructive changes
4. Assess cost implications if possible
5. Warn about any security concerns

## IMPORTANT:
- Never run `terraform` directly, always use `make` commands
- Review plans carefully before applying
- Production changes require extra scrutiny
