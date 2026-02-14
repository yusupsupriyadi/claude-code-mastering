# Infrastructure Management Rules

## Terraform Operations

- **ALWAYS** use Make commands for Terraform operations, never run Terraform directly
- **ALWAYS** update infrastructure using Terraform (except when fixing plan/apply errors)
- **NEVER** change infrastructure without Terraform

## Environment-specific Commands

```bash
# Development environment
make plan-wp AWS_PROFILE=your-dev-profile TARGET_ENV=dev

# Production environment
make plan-wp AWS_PROFILE=your-prod-profile TARGET_ENV=prod
```

## Best Practices

- Always specify the correct AWS_PROFILE and TARGET_ENV parameters
- Review Terraform plans carefully before applying changes
- Use appropriate environment-specific configurations

## Required Tools

- Docker and Docker Compose for local development
- Make for build automation and infrastructure management
- Appropriate AWS CLI configuration with named profiles
