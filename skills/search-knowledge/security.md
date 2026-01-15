# Security

## Secrets Management

- Use `secrets` module for tokens and keys
- `secrets.token_urlsafe()` for URL-safe tokens
- `secrets.compare_digest()` for timing-safe comparison
- Never hardcode secrets—use environment variables
- Use `.env` files locally, never commit them

## Password Handling

- Never store plaintext passwords
- Use `bcrypt`, `argon2`, or `passlib`
- Salt is included in modern hashing libraries
- Use constant-time comparison for verification

## Input Validation

- Validate all external input
- Use parameterized queries—never string interpolation
- Sanitize file paths—prevent traversal attacks
- Whitelist allowed values over blacklisting
- Limit input sizes to prevent DoS

## SQL Injection Prevention

- Use ORM methods—they parameterize automatically
- For raw SQL: `cursor.execute(query, params)`
- Never: `f"SELECT * FROM users WHERE id = {user_id}"`
- Always: `cursor.execute("SELECT * FROM users WHERE id = ?", (user_id,))`

## Common Anti-Patterns

- `eval()` or `exec()` with user input—never
- `pickle.load()` on untrusted data—use JSON
- Logging sensitive data—redact passwords, tokens
- Disabled SSL verification—never in production
- Hardcoded credentials—use environment variables
- `random` for security—use `secrets` instead
