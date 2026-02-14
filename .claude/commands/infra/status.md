---
description: Check infrastructure status and resources
allowed-tools: Bash(aws:*), Bash(terraform:*)
argument-hint: "[environment: dev|stg|prod]"
---

Check current infrastructure status.

Environment: $1

## Checks to perform:

### ECS Services
```bash
aws ecs list-services --cluster your-project-$1-cluster --region ap-northeast-1
aws ecs describe-services --cluster your-project-$1-cluster --services <service-name> --region ap-northeast-1
```

### Lambda Functions
```bash
aws lambda list-functions --region ap-northeast-1 --query "Functions[?contains(FunctionName, '$1')]"
```

### RDS Status
```bash
aws rds describe-db-instances --region ap-northeast-1
```

### CloudWatch Alarms
```bash
aws cloudwatch describe-alarms --region ap-northeast-1 --alarm-name-prefix your-project-$1
```

Report the status of all services and highlight any issues.
