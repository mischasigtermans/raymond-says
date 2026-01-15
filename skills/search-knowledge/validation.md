# Validation & Type Hints

## Type Hints

- Always type function signatures in production code
- Use `-> None` for functions that don't return
- Prefer `list[str]` over `List[str]` (3.9+)
- Use `|` for unions: `str | None` over `Optional[str]` (3.10+)
- `TypeAlias` for complex type definitions
- Avoid `Any`—it defeats the purpose

## Pydantic Models

- Use Pydantic for external data validation
- `BaseModel` for API request/response schemas
- Validators run automatically on instantiation
- Use `Field()` for constraints and defaults
- `model_dump()` over `.dict()` (Pydantic v2)
- `ConfigDict(strict=True)` for strict type coercion

## Dataclasses for Internal Data

- Use `dataclass` for internal data structures
- Add `__post_init__` for validation logic
- Use `field(default_factory=list)` for mutable defaults
- Consider `attrs` for more features

## Input Handling

- Validate at boundaries—not throughout code
- Parse, don't validate (convert early to typed structures)
- Use `isinstance()` checks sparingly—prefer duck typing
- Strip and normalize strings at entry points

## Common Anti-Patterns

- Passing dicts through the codebase—use typed models
- Validation scattered in business logic—centralize at boundaries
- Ignoring type checker errors—fix or properly annotate
- Using `# type: ignore` without comment explaining why
- Manual JSON parsing—use Pydantic
