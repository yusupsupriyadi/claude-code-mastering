# Frontend Development Rules

## Build Verification

- **ALWAYS** verify the frontend builds successfully with `npm run build`
- **NEVER** commit or deploy code with TypeScript compilation errors

## Code Quality Commands

```bash
# Lint code
npm run lint

# Fix lint errors
npm run lint:fix

# Check formatting
npm run format:check

# Format code
npm run format

# Run tests
npm run test
```

## Pre-commit Checklist

Before committing frontend changes:

1. `npm run build` - Verify production build succeeds
2. `npm run lint` - Ensure no linting errors
3. `npm run format:check` - Verify code formatting compliance
4. `npm run test` - Ensure all tests pass

## Development

- Start development server with `npm run dev` (port 3001)
- Use Storybook for component development: `npm run storybook`
- Verify environment variables required for production are properly configured
- Check that build output in `dist/` directory is generated successfully
