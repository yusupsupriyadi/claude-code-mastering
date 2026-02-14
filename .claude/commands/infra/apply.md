---
description: Apply Terraform changes (requires confirmation)
allowed-tools: Bash(make:*)
argument-hint: "[environment: dev|stg|prod]"
---

Apply Terraform changes to infrastructure.

Environment: $1

## CAUTION:
This will modify real infrastructure. Ensure you have:
1. Run `/infra/plan $1` first
2. Reviewed all planned changes
3. Confirmed destructive changes are intentional
4. Verified correct AWS profile is set

## Execute:
```bash
make apply-$1
```

## Post-apply:
1. Verify deployment succeeded
2. Check service health
3. Monitor for any errors
4. Update documentation if needed
