# Python Anti-Patterns

Code smells Raymond would flag immediately. Each includes the transformation.

---

## Loop Anti-Patterns

### 1. Manual Index Management
```python
# Anti-pattern
for i in range(len(items)):
    print(items[i])

# Pythonic
for item in items:
    print(item)
```
> "Whenever you find yourself manipulating indices, you're probably doing it wrong."

### 2. Index When You Need Index + Value
```python
# Anti-pattern
for i in range(len(items)):
    print(i, items[i])

# Pythonic
for i, item in enumerate(items):
    print(i, item)
```

### 3. Parallel Iteration
```python
# Anti-pattern
for i in range(len(names)):
    print(names[i], ages[i])

# Pythonic
for name, age in zip(names, ages):
    print(name, age)
```

### 4. Reverse Iteration
```python
# Anti-pattern
for i in range(len(items) - 1, -1, -1):
    print(items[i])

# Pythonic
for item in reversed(items):
    print(item)
```

---

## Class Anti-Patterns

### 5. Classes That Should Be Functions
```python
# Anti-pattern
class Validator:
    def __init__(self, data):
        self.data = data

    def validate(self):
        return len(self.data) > 0

# Pythonic
def validate(data):
    return len(data) > 0
```
> "If your class only has two methods and one is __init__, you probably meant to write a function."

### 6. Stateless Utility Classes
```python
# Anti-pattern
class StringUtils:
    @staticmethod
    def capitalize(s):
        return s.capitalize()

# Pythonic - just use the method
s.capitalize()
```

### 7. Java-Style Getters/Setters
```python
# Anti-pattern
class Rectangle:
    def __init__(self):
        self._length = 0

    def get_length(self):
        return self._length

    def set_length(self, value):
        self._length = value

# Pythonic - use property when needed
class Rectangle:
    def __init__(self):
        self.length = 0  # Just use attribute directly
```

---

## Data Structure Anti-Patterns

### 8. Dictionary When Named Tuple Fits
```python
# Anti-pattern
person = {'name': 'Alice', 'age': 30}

# Pythonic
from collections import namedtuple
Person = namedtuple('Person', ['name', 'age'])
person = Person('Alice', 30)

# Or with dataclass
from dataclasses import dataclass

@dataclass
class Person:
    name: str
    age: int
```

### 9. Manual Counting
```python
# Anti-pattern
counts = {}
for item in items:
    if item in counts:
        counts[item] += 1
    else:
        counts[item] = 1

# Pythonic
from collections import Counter
counts = Counter(items)
```
> "There's two kinds of people: those who've mastered dictionaries and total goobers."

### 10. Manual Defaulting
```python
# Anti-pattern
d = {}
for name in names:
    key = len(name)
    if key not in d:
        d[key] = []
    d[key].append(name)

# Pythonic
from collections import defaultdict
d = defaultdict(list)
for name in names:
    d[len(name)].append(name)
```

### 11. Using Lists as Queues
```python
# Anti-pattern - O(n) for pop(0)
queue = []
queue.append('item')
item = queue.pop(0)

# Pythonic - O(1) operations
from collections import deque
queue = deque()
queue.append('item')
item = queue.popleft()
```

---

## Exception Anti-Patterns

### 12. Bare Except
```python
# Anti-pattern
try:
    risky_operation()
except:
    pass

# Pythonic
try:
    risky_operation()
except SpecificException as e:
    handle_error(e)
```
> "Errors should never pass silently."

### 13. Exception Swallowing
```python
# Anti-pattern
try:
    value = int(user_input)
except ValueError:
    value = None  # Silent failure

# Pythonic
try:
    value = int(user_input)
except ValueError:
    raise ValueError(f"Invalid input: {user_input}")
```

---

## String Anti-Patterns

### 14. String Concatenation in Loops
```python
# Anti-pattern - quadratic!
result = ""
for item in items:
    result += str(item)

# Pythonic
result = "".join(str(item) for item in items)
```

### 15. Manual String Formatting
```python
# Anti-pattern
message = "Hello " + name + ", you are " + str(age)

# Pythonic
message = f"Hello {name}, you are {age}"
```
> "f-strings are amazingly fast!"

---

## Mutability Anti-Patterns

### 16. Mutable Default Arguments
```python
# Anti-pattern
def append_to(item, target=[]):
    target.append(item)
    return target

# Pythonic
def append_to(item, target=None):
    if target is None:
        target = []
    target.append(item)
    return target
```

### 17. Modifying While Iterating
```python
# Anti-pattern
for key in d:
    if should_remove(key):
        del d[key]  # RuntimeError!

# Pythonic
d = {k: v for k, v in d.items() if not should_remove(k)}
```
> "If you mutate something while iterating over it, you're living in a state of sin."

---

## Import Anti-Patterns

### 18. Star Imports
```python
# Anti-pattern
from module import *

# Pythonic
from module import specific_function, SpecificClass
```

### 19. Reimplementing Standard Library
```python
# Anti-pattern
def flatten(nested_list):
    result = []
    for item in nested_list:
        if isinstance(item, list):
            result.extend(flatten(item))
        else:
            result.append(item)
    return result

# Pythonic - for one level
from itertools import chain
list(chain.from_iterable(nested_list))
```
> "Check if the standard library has it before writing."

---

## Flow Control Anti-Patterns

### 20. Loop Flags Instead of any()/all()
```python
# Anti-pattern
found = False
for item in items:
    if condition(item):
        found = True
        break

# Pythonic
found = any(condition(item) for item in items)
```

### 21. map/filter with Lambda
```python
# Anti-pattern
squares = list(map(lambda x: x ** 2, numbers))
evens = list(filter(lambda x: x % 2 == 0, numbers))

# Pythonic
squares = [x ** 2 for x in numbers]
evens = [x for x in numbers if x % 2 == 0]
```

---

## Generator Anti-Patterns

### 22. Loading Everything Into Memory
```python
# Anti-pattern
def get_squares(n):
    result = []
    for i in range(n):
        result.append(i ** 2)
    return result

# Pythonic
def get_squares(n):
    for i in range(n):
        yield i ** 2
```

### 23. List Comprehension When Generator Suffices
```python
# Anti-pattern
sum([x ** 2 for x in range(1000000)])  # Creates list in memory

# Pythonic
sum(x ** 2 for x in range(1000000))  # Generator expression
```

---

## Over-Engineering Anti-Patterns

### 24. Premature Abstraction
```python
# Anti-pattern: Planning hierarchy upfront
class BaseProcessor:
    def process(self): ...

class DataProcessor(BaseProcessor):
    def process(self): ...

class AdvancedDataProcessor(DataProcessor):
    def process(self): ...

# Pythonic: Let design emerge from use cases
def process_data(data):
    # Just do the thing
    return transformed_data
```
> "Designing up front is really difficult. Designing after you have concrete use cases is trivial."
