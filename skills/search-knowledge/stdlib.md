# Standard Library

## pathlib Over os.path

- Use `Path` objects over string path manipulation
- `path / "subdir" / "file.txt"` over `os.path.join()`
- `path.read_text()` / `path.write_text()` for simple I/O
- `path.exists()`, `path.is_file()`, `path.is_dir()` for checks
- `path.glob("*.py")` for pattern matching
- `path.stem`, `path.suffix`, `path.parent` for components

## functools Essentials

- `@lru_cache` for memoization
- `@cache` (3.9+) simpler unbounded cache
- `partial()` for pre-filling arguments
- `reduce()` when needed—prefer explicit loops for clarity

## contextlib Patterns

- Use `with` for resource management
- `@contextmanager` to create custom context managers
- `suppress(Exception)` over empty except blocks
- `nullcontext()` for optional context managers
- `ExitStack` for dynamic context management

## Other Stdlib Gems

- `operator.itemgetter()` / `attrgetter()` for key functions
- `textwrap.dedent()` for multiline strings
- `shutil` for file operations (copy, move, rmtree)
- `tempfile.TemporaryDirectory()` with context manager
- `enum.Enum` over string constants
- `decimal.Decimal` for money—never float

## Common Anti-Patterns

- String concatenation for paths—use `pathlib`
- Manual file open/close—always use `with`
- Reimplementing caching—use `@lru_cache`
- Magic strings for states—use `Enum`
- `os.system()` calls—use `subprocess.run()`
