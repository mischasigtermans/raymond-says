# Data Structures

## Dictionary Patterns

- Use `dict.get(key, default)` over `if key in dict`
- Use `dict.setdefault(key, []).append(val)` for grouping
- Prefer `collections.defaultdict` for repeated defaults
- Use `dict.pop(key, None)` for safe removal
- Merge with `{**a, **b}` or `a | b` (3.9+)
- Use `dict.items()` for iteration—not `.keys()` + lookup

## Sets for Membership

- Use `set` for O(1) membership tests
- Prefer `if x in my_set` over `if x in my_list`
- Set operations: `a & b` (intersection), `a | b` (union), `a - b` (difference)
- Use `set.discard()` for removal that won't raise

## Named Structures

- Prefer `dataclass` over plain `class` for data containers
- Use `frozen=True` for immutable dataclasses
- `namedtuple` for simple immutable records
- `typing.NamedTuple` for typed named tuples
- Avoid dicts for structured data—use dataclasses

## Collections Module

- `Counter` for counting hashables
- `deque` for O(1) append/pop both ends
- `OrderedDict` rarely needed (dicts preserve order 3.7+)
- `ChainMap` for layered lookups

## Common Anti-Patterns

- Using list for membership checks—O(n) vs set O(1)
- Nested dicts for structured data—use dataclass
- Manual counting loops—use `Counter`
- Mutable default arguments—never `def f(items=[])`
- Building dict from parallel lists—use `zip()`
