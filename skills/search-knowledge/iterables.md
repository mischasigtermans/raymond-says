# Iterables & Generators

## Comprehensions Over Loops

- Prefer `[x.name for x in users]` over `for` + `append`
- Use `{x for x in items}` for unique values
- Dict comprehensions: `{k: v for k, v in pairs}`
- Nested comprehensions read left-to-right like nested loops

## Generator Expressions

- Use `(x for x in items)` for single-pass iteration
- Generators don't build full list in memory
- Prefer `sum(x for x in items)` over `sum([x for x in items])`
- Use `any(cond for x in items)` over loop with flag
- Use `all(cond for x in items)` for universal checks

## itertools Essentials

- `itertools.chain()` to flatten iterables without intermediate list
- `itertools.islice()` for slicing generators
- `itertools.batched()` (3.12+) for chunking
- `itertools.groupby()` for consecutive grouping (sort first!)
- `itertools.takewhile()` / `dropwhile()` for conditional slicing
- `itertools.zip_longest()` when lengths differ

## Lazy Evaluation

- Prefer generators for large data processing
- Chain generators: `filtered = (x for x in items if cond)`
- Only materialize with `list()` when needed
- Use `next(iter, default)` for first-or-default

## Common Anti-Patterns

- Building list just to iterate once—use generator
- `len(list(generator))` wastes memory—use `sum(1 for _ in gen)`
- Indexing into generator—convert to list or rethink approach
- Multiple passes over generator—use `itertools.tee()` or materialize
