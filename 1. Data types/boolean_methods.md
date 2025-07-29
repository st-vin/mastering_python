## Boolean (`bool`) Methods & Operations

| Method/Operation | Description                        | Usage Example                                          |
| ---------------- | ---------------------------------- | ------------------------------------------------------ |
| `and`            | Logical AND operation              | `True and False` → `False`                             |
| `or`             | Logical OR operation               | `True or False` → `True`                               |
| `not`            | Logical NOT operation              | `not True` → `False`                                   |
| `==`             | Equality comparison                | `True == 1` → `True`                                   |
| `!=`             | Inequality comparison              | `True != False` → `True`                               |
| `bool()`         | Converts value to boolean          | `bool("hello")` → `True`, `bool("")` → `False`         |
| `int()`          | Converts to integer                | `int(True)` → `1`, `int(False)` → `0`                  |
| `str()`          | Converts to string                 | `str(True)` → `'True'`                                 |
| Short-circuit    | Logical operators short-circuit    | `False and expensive_function()` (function not called) |
| Truthiness       | Any object can be tested for truth | `bool([1, 2, 3])` → `True`, `bool([])` → `False`       |
| Conditional      | Used in if statements              | `if user_logged_in: print("Welcome!")`                 |