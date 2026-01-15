# APIs & Web Frameworks

## FastAPI Patterns

- Use Pydantic models for request/response
- Dependency injection via `Depends()`
- Path parameters with type hints auto-validate
- Use `HTTPException` for error responses
- Background tasks via `BackgroundTasks`
- OpenAPI docs generated automatically

## Flask Patterns

- Use blueprints for modular apps
- `@app.route` with methods parameter
- `request.json` for JSON bodies
- `jsonify()` for responses
- Use `flask.g` for request-scoped globals
- Factory pattern with `create_app()`

## Django Patterns

- Fat models, thin views
- Use class-based views for CRUD
- `get_object_or_404()` over manual try/except
- QuerySet chaining for complex queries
- Use `select_related()` / `prefetch_related()` to avoid N+1
- Signals sparingly—explicit is better

## General API Design

- Return appropriate HTTP status codes
- Validate input at the boundary
- Use typed response models
- Handle errors consistently
- Log requests and errors
- Keep handlers thin—delegate to services

## Common Anti-Patterns

- Business logic in route handlers—extract to services
- Returning bare dicts—use typed models
- Catching all exceptions silently—let errors propagate
- N+1 queries in list endpoints—eager load
- Hardcoded URLs—use url_for or route names
- No input validation—use Pydantic or framework validators
