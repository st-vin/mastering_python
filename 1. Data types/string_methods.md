## String (`str`) Methods

| Method/Operation | Description                                         | Usage Example                                                                      |
| ---------------- | --------------------------------------------------- | ---------------------------------------------------------------------------------- |
| `split()`        | Splits string into list based on delimiter          | `"hello,world,python".split(",")` → `['hello', 'world', 'python']`                 |
| `join()`         | Joins iterable elements into single string          | `"-".join(['2024', '01', '15'])` → `'2024-01-15'`                                  |
| `strip()`        | Removes whitespace from both ends                   | `" hello world ".strip()` → `'hello world'`                                        |
| `replace()`      | Replaces occurrences of substring                   | `"Hello World".replace("World", "Python")` → `'Hello Python'`                      |
| `find()`         | Returns index of first occurrence (-1 if not found) | `"python@email.com".find("@")` → `6`                                               |
| `startswith()`   | Checks if string starts with specified prefix       | `"filename.txt".startswith("file")` → `True`                                       |
| `endswith()`     | Checks if string ends with specified suffix         | `"document.pdf".endswith(".pdf")` → `True`                                         |
| `lower()`        | Converts to lowercase                               | `"USERNAME".lower()` → `'username'`                                                |
| `upper()`        | Converts to uppercase                               | `"password".upper()` → `'PASSWORD'`                                                |
| `format()`       | Formats string with placeholders                    | `"Hello {name}, age {age}".format(name="Alice", age=30)` → `'Hello Alice, age 30'` |
| `isdigit()`      | Checks if all characters are digits                 | `"12345".isdigit()` → `True`                                                       |
| `count()`        | Counts occurrences of substring                     | `"hello hello world".count("hello")` → `2`                                         |
| `len()`          | Returns length of string                            | `len("Hello World")` → `11`                                                        |
| `in`             | Checks if substring exists                          | `"@" in "user@domain.com"` → `True`                                                |
| `+`              | Concatenates strings                                | `"Hello " + "World"` → `'Hello World'`                                             |
