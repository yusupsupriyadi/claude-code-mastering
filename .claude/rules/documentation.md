# Documentation Rules

## Technical Documentation Location

All technical documentation is in `docs/`:

```
docs/
├── README.md                    # Overview and quick navigation
├── architecture/                # Core system architecture
├── deployment/                  # CI/CD and deployment
├── observability/               # Monitoring and logging
└── planned-features/            # Future enhancements
```

## Documentation Guidelines

When making implementation changes, **ALWAYS** update the corresponding documentation:

1. **Feature Changes**: Update the relevant architecture document in `docs/`
2. **New Features**: Create documentation before or during implementation
3. **Status Updates**: Use status badges at the top of each document:
   - `> **Status: IMPLEMENTED**` - Fully deployed in production
   - `> **Status: IN DEVELOPMENT**` - Currently being built
   - `> **Status: PLANNED**` - Designed but not started
4. **Language**: All documentation must be in English
5. **Cross-references**: Update links when moving or renaming documents

## Documentation Update Triggers

Update documentation when:

- Adding new API endpoints
- Changing infrastructure architecture
- Modifying logging or tracing systems
- Adding new integrations
- Changing deployment processes

## Code Comments

- Add comments for complex business logic only
- Maintain existing documentation standards
- Follow the established code comment style
- **All comments must be in English**
