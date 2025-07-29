## Tuple (`tuple`) Methods

| Method/Operation | Description                         | Usage Example                                   |
| ---------------- | ----------------------------------- | ----------------------------------------------- |
| `count()`        | Counts occurrences of value         | `(1, 2, 2, 3).count(2)` → `2`                   |
| `index()`        | Returns index of first occurrence   | `('a', 'b', 'c').index('b')` → `1`              |
| `len()`          | Returns number of elements          | `len(('apple', 'banana', 'cherry'))` → `3`      |
| `in`             | Checks if element exists            | `'apple' in ('apple', 'banana')` → `True`       |
| `+`              | Concatenates tuples                 | `(1, 2) + (3, 4)` → `(1, 2, 3, 4)`              |
| `*`              | Repeats tuple                       | `(1, 2) * 3` → `(1, 2, 1, 2, 1, 2)`             |
| `[index]`        | Accesses element by index           | `coordinates = (10, 20); coordinates[0]` → `10` |
| `[start:end]`    | Slices tuple                        | `(1, 2, 3, 4, 5)[1:4]` → `(2, 3, 4)`            |
| Unpacking        | Assigns tuple elements to variables | `point = (3, 4); x, y = point` → `x=3, y=4`     |