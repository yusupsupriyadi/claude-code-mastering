---
name: api-development
description: Assists with REST API endpoint development. Automatically activates when creating new API endpoints, routes, schemas, or services. Keywords: endpoint, api, route, rest, crud, schema
allowed-tools: Read, Write, Grep
---

## REST API Development Assistant

You are an expert in REST API development. Adapt to the project's framework (FastAPI, Express, Spring, etc.).

### Typical Project Structure
```
app/
├── api/              # API endpoints (routers/controllers)
├── models/           # Database models
├── schemas/          # Request/response schemas
├── services/         # Business logic
├── core/             # Core utilities (auth, config)
└── db/               # Database utilities
```

### API Patterns

**All endpoints must:**
- Use `/api/v1/` prefix
- Be async (`async def`)
- Include proper authentication
- Return consistent error formats
- Support pagination for list endpoints

### Creating a New Endpoint

1. **Define Pydantic schemas** (`app/schemas/`)
```python
from pydantic import BaseModel
from datetime import datetime
from uuid import UUID

class ItemBase(BaseModel):
    name: str
    description: str | None = None

class ItemCreate(ItemBase):
    pass

class ItemResponse(ItemBase):
    id: UUID
    created_at: datetime

    model_config = ConfigDict(from_attributes=True)
```

2. **Create router** (`app/api/v1/`)
```python
from fastapi import APIRouter, Depends, HTTPException
from sqlalchemy.ext.asyncio import AsyncSession
from app.core.auth import get_current_user
from app.db.session import get_db

router = APIRouter(prefix="/items", tags=["items"])

@router.get("/", response_model=list[ItemResponse])
async def list_items(
    db: AsyncSession = Depends(get_db),
    current_user: User = Depends(get_current_user),
    skip: int = 0,
    limit: int = 100,
):
    # Implementation
    pass

@router.post("/", response_model=ItemResponse, status_code=201)
async def create_item(
    item: ItemCreate,
    db: AsyncSession = Depends(get_db),
    current_user: User = Depends(get_current_user),
):
    # Implementation
    pass
```

3. **Register router** in `app/api/v1/__init__.py`

### Error Handling
```python
from fastapi import HTTPException

# Not found
raise HTTPException(status_code=404, detail="Item not found")

# Bad request
raise HTTPException(status_code=400, detail="Invalid input")

# Forbidden
raise HTTPException(status_code=403, detail="Not authorized")
```

### Authentication
```python
from app.core.auth import get_current_user

@router.get("/protected")
async def protected_endpoint(
    current_user: User = Depends(get_current_user)
):
    return {"user_id": current_user.id}
```

### Best Practices
- Use dependency injection for database sessions
- Validate input with Pydantic models
- Return proper HTTP status codes
- Include OpenAPI documentation
- Add proper type hints
- Write tests for all endpoints
