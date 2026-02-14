---
name: database-migration
description: Assists with PostgreSQL database migrations using Alembic. Automatically activates when working with schema changes, table creation, column modifications, index creation, or migration files. Keywords: migration, alembic, schema, database, table, column, index, foreign key
allowed-tools: Read, Write, Bash(docker compose exec:*), Bash(make:*)
---

## Database Migration Assistant

You are an expert in PostgreSQL database migrations using Alembic with SQLAlchemy 2.0.

### Project Structure
- Models: `app/models/`
- Migrations: `alembic/versions/`
- Alembic config: `alembic.ini`

### Migration Workflow

1. **Create New Migration**
   ```bash
   make makemigrations
   ```

2. **Review Migration**
   - Check the generated file in `alembic/versions/`
   - Verify upgrade() and downgrade() functions
   - Ensure data migration if needed

3. **Apply Migration**
   ```bash
   make migrate
   ```

4. **Check Status**
   ```bash
   docker compose exec app uv run alembic current
   docker compose exec app uv run alembic history
   ```

### Best Practices
- Always create reversible migrations
- Use batch operations for large data changes
- Consider data integrity during schema changes
- Test migrations on development first
- Add indexes for frequently queried columns
- Use appropriate column types and constraints

### Common Patterns

**Adding a new table:**
```python
def upgrade():
    op.create_table(
        'table_name',
        sa.Column('id', sa.UUID(), primary_key=True),
        sa.Column('created_at', sa.DateTime(), server_default=sa.func.now()),
        sa.Column('updated_at', sa.DateTime(), onupdate=sa.func.now()),
    )

def downgrade():
    op.drop_table('table_name')
```

**Adding a column:**
```python
def upgrade():
    op.add_column('table_name', sa.Column('new_column', sa.String(255)))

def downgrade():
    op.drop_column('table_name', 'new_column')
```

**Adding an index:**
```python
def upgrade():
    op.create_index('ix_table_column', 'table_name', ['column_name'])

def downgrade():
    op.drop_index('ix_table_column')
```
