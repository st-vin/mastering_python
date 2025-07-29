## Dictionary (`dict`) Methods

| Method/Operation | Description                                   | Usage Example                                                                       |
| ---------------- | --------------------------------------------- | ----------------------------------------------------------------------------------- |
| `get()`          | Returns value for key (with optional default) | `user = {'name': 'John'}; user.get('age', 0)` → `0`                                 |
| `keys()`         | Returns view of dictionary keys               | `{'a': 1, 'b': 2}.keys()` → `dict_keys(['a', 'b'])`                                 |
| `values()`       | Returns view of dictionary values             | `{'a': 1, 'b': 2}.values()` → `dict_values([1, 2])`                                 |
| `items()`        | Returns view of key-value pairs               | `{'a': 1, 'b': 2}.items()` → `dict_items([('a', 1), ('b', 2)])`                     |
| `pop()`          | Removes key and returns its value             | `data = {'x': 10, 'y': 20}; data.pop('x')` → `10`                                   |
| `popitem()`      | Removes and returns last key-value pair       | `data = {'a': 1}; data.popitem()` → `('a', 1)`                                      |
| `update()`       | Updates dictionary with another dict/iterable | `user = {'name': 'John'}; user.update({'age': 30})` → `{'name': 'John', 'age': 30}` |
| `clear()`        | Removes all items                             | `data = {'a': 1}; data.clear()` → `{}`                                              |
| `copy()`         | Creates shallow copy                          | `original = {'a': 1}; backup = original.copy()`                                     |
| `setdefault()`   | Returns value or sets default if key missing  | `counts = {}; counts.setdefault('apple', 0)` → `0`                                  |
| `len()`          | Returns number of key-value pairs             | `len({'a': 1, 'b': 2})` → `2`                                                       |
| `in`             | Checks if key exists                          | `'name' in {'name': 'John', 'age': 30}` → `True`                                    |
| `[key]`          | Accesses/sets value by key                    | `person = {'name': 'Alice'}; person['age'] = 25`                                    |
| `del`            | Removes key-value pair                        | `data = {'x': 1, 'y': 2}; del data['x']` → `{'y': 2}`                               |