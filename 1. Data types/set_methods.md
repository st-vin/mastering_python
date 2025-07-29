## Set (`set`) Methods

| Method/Operation                | Description                                    | Usage Example                                              |
| ------------------------------- | ---------------------------------------------- | ---------------------------------------------------------- |
| `add()`                         | Adds single element to set                     | `colors = {'red'}; colors.add('blue')` → `{'red', 'blue'}` |
| `update()`                      | Adds multiple elements from iterable           | `nums = {1, 2}; nums.update([3, 4])` → `{1, 2, 3, 4}`      |
| `remove()`                      | Removes element (raises KeyError if not found) | `items = {'a', 'b'}; items.remove('a')` → `{'b'}`          |
| `discard()`                     | Removes element (no error if not found)        | `items = {'a', 'b'}; items.discard('c')` → `{'a', 'b'}`    |
| `pop()`                         | Removes and returns arbitrary element          | `numbers = {1, 2, 3}; numbers.pop()` → random element      |
| `clear()`                       | Removes all elements                           | `data = {1, 2, 3}; data.clear()` → `set()`                 |
| `copy()`                        | Creates shallow copy                           | `original = {1, 2}; backup = original.copy()`              |
| `union()` or `\|`               | Returns union of sets                          | `{1, 2}.union({2, 3})` → `{1, 2, 3}`                       |
| `intersection()` or `&`         | Returns intersection of sets                   | `{1, 2, 3} & {2, 3, 4}` → `{2, 3}`                         |
| `difference()` or `-`           | Returns difference of sets                     | `{1, 2, 3} - {2, 4}` → `{1, 3}`                            |
| `symmetric_difference()` or `^` | Returns symmetric difference                   | `{1, 2} ^ {2, 3}` → `{1, 3}`                               |
| `issubset()`                    | Checks if set is subset of another             | `{1, 2}.issubset({1, 2, 3})` → `True`                      |
| `issuperset()`                  | Checks if set is superset of another           | `{1, 2, 3}.issuperset({1, 2})` → `True`                    |
| `len()`                         | Returns number of elements                     | `len({1, 2, 3})` → `3`                                     |
| `in`                            | Checks if element exists                       | `2 in {1, 2, 3}` → `True`                                  |