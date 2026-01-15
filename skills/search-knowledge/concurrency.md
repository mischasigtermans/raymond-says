# Concurrency

## asyncio Basics

- Use `async`/`await` for I/O-bound concurrency
- `asyncio.run()` as entry point
- `await asyncio.gather()` for parallel async calls
- `asyncio.create_task()` for background tasks
- Use `async with` for async context managers
- `asyncio.Queue` for producer-consumer patterns

## When to Use What

- **asyncio**: I/O-bound, many concurrent connections
- **threading**: I/O-bound, simpler mental model, existing sync libs
- **multiprocessing**: CPU-bound, need true parallelism
- **concurrent.futures**: Simple parallel execution

## Threading

- Use `threading.Thread` for simple parallelism
- `concurrent.futures.ThreadPoolExecutor` for pooling
- Protect shared state with `Lock` or `RLock`
- Use `Queue` for thread-safe communication
- GIL limits CPU parallelism—threads don't help CPU-bound work

## Multiprocessing

- Use for CPU-bound parallelism
- `ProcessPoolExecutor` for simple cases
- Data must be picklable
- Higher overhead than threads
- `multiprocessing.Queue` for IPC

## Common Anti-Patterns

- Mixing sync and async incorrectly—blocks event loop
- Calling `asyncio.run()` inside async function
- Bare threads without cleanup—use executors
- Shared mutable state without locks
- CPU-bound work in asyncio—use `run_in_executor()`
- Ignoring `await` on coroutines—silent failures
