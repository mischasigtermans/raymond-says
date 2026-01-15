# Raymond Says

Claude Code plugin channeling Raymond Hettinger's Pythonic philosophy. "There must be a better way!"

Raymond reviews your Python code for anti-patterns, Java-isms, and missed opportunities to use Python idiomatically. Enthusiastic, teaching-oriented, and genuinely excited about beautiful code.

Available through the [Ryde Ventures plugin marketplace](https://github.com/rydeventures/claude-plugins).

## Installation

```
# Add the Ryde Ventures marketplace (one-time)
/plugin marketplace add rydeventures/claude-plugins

# Install the plugin
/plugin install raymond-says@rydeventures-claude-plugins
```

## Quick Start

```
# Review uncommitted changes (default behavior)
@raymond

# Review a specific file
@raymond review src/services/user_service.py

# Simplify uncommitted changes (applies fixes directly)
@raymond simplify

# Simplify a specific file
@raymond simplify src/utils.py

# Hunt for Java-isms in your codebase
@raymond find classes that should be functions

# Review an entire directory
@raymond review all files in src/

# Find anti-patterns
@raymond check for mutable default arguments
```

## Modes

| Mode | Command | Behavior |
|------|---------|----------|
| **Review** | `@raymond` | Analyze, give feedback, no changes |
| **Simplify** | `@raymond simplify` | Analyze AND apply fixes directly |

Simplify mode focuses on Pythonic transformations: converting manual loops to comprehensions, replacing classes-that-should-be-functions with functions, fixing mutable default arguments, and using the standard library.

## What Raymond Looks For

### Red Flags
- `for i in range(len(x))` instead of direct iteration
- Classes with only `__init__` and one method
- Manual counting instead of `Counter`
- Dicts with fixed keys instead of `dataclass`
- Java-style getters/setters

### The Pythonic Way
- Direct iteration and comprehensions
- Functions over unnecessary classes
- Standard library (collections, itertools, functools)
- f-strings for formatting
- Generators for large sequences

## Example Review

**Input:** A `UserService` class with Java-style patterns

```python
class UserService:
    def __init__(self, db):
        self.db = db

    def get_active_users(self):
        result = []
        for i in range(len(self.db.users)):
            user = self.db.users[i]
            if user.is_active == True:
                result.append(user)
        return result

    def get_user_names(self, users):
        names = []
        for user in users:
            names.append(user.name)
        return names
```

**Raymond says:**

> ### Overall Assessment
>
> This is Java copied into Python. The patterns here fight the language instead of embracing it. Python has beautiful, expressive ways to do exactly what you're doing - let me show you.
>
> ### Anti-Patterns Found
>
> **Manual loop with `range(len())`** - This is the classic sign of someone thinking in C or Java. Python iterates directly over collections.
>
> **Building lists with append loops** - Every time you write `result = []` followed by a loop with `append`, there's almost certainly a list comprehension waiting to be born.
>
> **Comparing to `True` explicitly** - `if user.is_active == True` should just be `if user.is_active`. Boolean values ARE booleans.
>
> **Class that should be functions** - `UserService` has no meaningful state after `__init__`. These are just functions pretending to be a class.
>
> ### The Pythonic Way
>
> ```python
> def get_active_users(users):
>     return [user for user in users if user.is_active]
>
> def get_user_names(users):
>     return [user.name for user in users]
> ```
>
> Look at that. Four lines instead of fifteen. No class, no `self`, no manual iteration. This is what Python wants to be.
>
> ### Closing
>
> There must be a better way... and now you've seen it. The list comprehension is one of Python's crown jewels - use it!

## Representative Quotes

> "Stop writing classes."

> "If you're manually managing indices, you're doing it wrong."

> "The standard library is vast and full of treasures."

> "This is not Python. This is Java that happens to run on the Python interpreter."

> "Transform your code. Don't just fix it."

## Knowledge System

Raymond automatically loads relevant knowledge based on what you're reviewing:

| File Pattern | Knowledge |
|--------------|-----------|
| Loops, iteration | Generators, comprehensions, itertools |
| Classes, objects | Dataclasses, namedtuples, when to use classes |
| Dicts, sets, lists | Collections module, proper data structure choice |
| File handling | pathlib, context managers |
| Type hints | Pydantic, typing module, validation patterns |
| Testing | pytest, fixtures, mocking best practices |
| Async code | asyncio, threading, multiprocessing |
| Web frameworks | Flask, FastAPI, Django patterns |

## Philosophy

Raymond's code philosophy centers on:

1. **Teaching over telling** - Shows transformations, not just problems
2. **Pythonic idioms** - Use the language as designed
3. **Standard library first** - Check if it exists before writing
4. **Simplicity** - Functions over classes when classes add nothing
5. **Readability** - Code is read far more than it's written

> "There must be a better way!"
> — Raymond Hettinger

## Benchmarks

Every release is benchmarked with **18 parallel Raymond agents** reviewing **6 different Python features** to ensure:

| Metric | Current (v0.1.0) |
|--------|:----------------:|
| Consistency | — |
| Authenticity | —/10 |
| Technical Depth | —/10 |
| Teaching Quality | —/10 |

See [BENCHMARK.md](BENCHMARK.md) for methodology and version history.

> **Note:** Detailed benchmark reports, research materials, and prompt engineering artifacts are kept internal. The published plugin represents our best refinement of Raymond's voice and technical accuracy.

## Requirements

- [Claude Code](https://claude.com/claude-code)
- A Python codebase

## Credits

- [Mischa Sigtermans](https://github.com/mischasigtermans)
- Philosophy: [Raymond Hettinger](https://github.com/rhettinger)

## License

MIT
