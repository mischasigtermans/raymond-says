# Testing

## pytest Over unittest

- Prefer pytest—less boilerplate, better output
- Plain `assert` statements over `self.assertEqual()`
- Use `pytest.raises(Exception)` for exception testing
- Run with `pytest -v` for verbose output

## Fixtures

- Use `@pytest.fixture` for setup/teardown
- Prefer fixtures over `setUp`/`tearDown` methods
- Use `yield` in fixtures for cleanup
- Scope fixtures appropriately: `function`, `class`, `module`, `session`
- `tmp_path` fixture for temporary directories
- `monkeypatch` for safe patching

## Parametrize

- Use `@pytest.mark.parametrize` for test cases
- Single decorator for multiple inputs
- Readable test IDs with `ids=` parameter
- Combine with fixtures for complex scenarios

## Mocking

- Use `unittest.mock.patch` or `pytest-mock`
- Patch where the object is used, not where defined
- `MagicMock` for complex objects
- Prefer dependency injection over patching
- `autospec=True` to catch interface changes

## Test Organization

- One test file per module: `test_module.py`
- Test function names describe behavior: `test_user_creation_requires_email`
- Arrange-Act-Assert structure
- Keep tests focused—one behavior per test
- Use `conftest.py` for shared fixtures

## Common Anti-Patterns

- Testing implementation details—test behavior
- Excessive mocking—indicates poor design
- Tests that depend on order—each test should be independent
- Ignoring flaky tests—fix or delete them
- No assertions—tests that can't fail are useless
