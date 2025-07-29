## List (`list`) Methods

| Method/Operation | Description                                          | Usage Example                                                               |
| ---------------- | ---------------------------------------------------- | --------------------------------------------------------------------------- |
| `append()`       | Adds single element to end                           | `fruits = ['apple']; fruits.append('banana')` → `['apple', 'banana']`       |
| `extend()`       | Adds all elements from iterable                      | `nums = [1, 2]; nums.extend([3, 4])` → `[1, 2, 3, 4]`                       |
| `insert()`       | Inserts element at specified index                   | `items = ['a', 'c']; items.insert(1, 'b')` → `['a', 'b', 'c']`              |
| `remove()`       | Removes first occurrence of value                    | `colors = ['red', 'blue', 'red']; colors.remove('red')` → `['blue', 'red']` |
| `pop()`          | Removes and returns element at index (default: last) | `stack = [1, 2, 3]; stack.pop()` → `3`, stack becomes `[1, 2]`              |
| `index()`        | Returns index of first occurrence                    | `['a', 'b', 'c'].index('b')` → `1`                                          |
| `count()`        | Counts occurrences of value                          | `[1, 2, 2, 3].count(2)` → `2`                                               |
| `sort()`         | Sorts list in place                                  | `nums = [3, 1, 2]; nums.sort()` → `[1, 2, 3]`                               |
| `reverse()`      | Reverses list in place                               | `items = [1, 2, 3]; items.reverse()` → `[3, 2, 1]`                          |
| `copy()`         | Creates shallow copy                                 | `original = [1, 2]; backup = original.copy()`                               |
| `clear()`        | Removes all elements                                 | `items = [1, 2, 3]; items.clear()` → `[]`                                   |
| `len()`          | Returns number of elements                           | `len(['a', 'b', 'c'])` → `3`                                                |
| `in`             | Checks if element exists                             | `'apple' in ['apple', 'banana']` → `True`                                   |
| `+`              | Concatenates lists                                   | `[1, 2] + [3, 4]` → `[1, 2, 3, 4]`                                          |
| `[index]`        | Accesses element by index                            | `fruits = ['apple', 'banana']; fruits[0]` → `'apple'`                       |