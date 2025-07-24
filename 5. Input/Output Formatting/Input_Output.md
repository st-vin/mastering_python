# Python Input/Output: Daily Developer Essentials

## String Formatting - The Bread and Butter

You'll spend a lot of time making strings look right. Python gives you three main ways to do this, and you'll probably use all of them depending on what you're building.

**F-strings are your go-to tool**. They're clean, readable, and fast. You just prefix your string with `f` and drop variables inside curly braces:

```python
name = "Sarah"
age = 28
print(f"Hello {name}, you are {age} years old")
```

Want to format numbers? F-strings handle that too:

```python
pi = 3.14159
print(f"Pi rounded to 2 places: {pi:.2f}")  # Pi rounded to 2 places: 3.14
```

You can align text, pad numbers, and even debug by showing variable names:

```python
bugs = "memory leaks"
count = 5
print(f"Debugging: {bugs=} {count=}")  # Shows: bugs='memory leaks' count=5
```

**The .format() method** is older but still useful when you need more complex formatting or when working with templates:

```python
template = "User {name} has {points} points"
result = template.format(name="John", points=150)
```

**Manual string formatting** with methods like `.rjust()`, `.ljust()`, and `.center()` comes in handy when you need precise control over spacing, especially for console output or reports.

## File Operations - Handle With Care

File handling is something you'll do constantly, whether reading config files, processing data, or logging output.

**Always use context managers** with the `with` statement. This ensures files get closed properly even if something goes wrong:

```python
with open('data.txt', 'r', encoding='utf-8') as f:
    content = f.read()
# File automatically closes here
```

**Know your file modes**:
- `'r'` for reading (default)
- `'w'` for writing (overwrites existing files)
- `'a'` for appending
- `'r+'` for both reading and writing
- Add `'b'` for binary mode when dealing with images, executables, etc.

**Reading strategies depend on file size**:
- `.read()` loads everything into memory - fine for small files
- `.readline()` reads one line at a time
- Looping over the file object is memory-efficient for large files:

```python
with open('large_file.txt') as f:
    for line in f:
        process_line(line)
```

**Writing is straightforward** but remember that `.write()` returns the number of characters written, not the content:

```python
with open('output.txt', 'w') as f:
    chars_written = f.write("Hello world\n")
```

## JSON - Your Data Exchange Format

JSON handling is essential for web APIs, configuration files, and data storage. Python makes this simple with the `json` module.

**Converting Python to JSON**:

```python
import json

data = {'name': 'Alice', 'scores': [85, 92, 78]}
json_string = json.dumps(data)  # Convert to string
```

**Writing JSON to files**:

```python
with open('data.json', 'w', encoding='utf-8') as f:
    json.dump(data, f)  # Write directly to file
```

**Reading JSON back**:

```python
with open('data.json', 'r', encoding='utf-8') as f:
    data = json.load(f)  # Load from file
```

**Important gotchas**:
- Always specify `encoding='utf-8'` for JSON files
- JSON can handle basic Python types (dict, list, string, number, boolean, None) but not custom objects without extra work
- Use `json.loads()` for strings, `json.load()` for files

## String Representation - Debug and Display

Understanding `str()` vs `repr()` helps with debugging and user interfaces:

- `str()` creates human-readable output
- `repr()` creates developer-readable output that should be valid Python code

```python
text = "Hello\nWorld"
print(str(text))   # Hello
                   # World
print(repr(text))  # 'Hello\nWorld'
```

This distinction matters when you're building logs, error messages, or debugging output.

## File Position Control

Sometimes you need to jump around in files. The `.seek()` and `.tell()` methods let you control where you're reading or writing:

```python
with open('file.txt', 'r+b') as f:  # Binary mode for seeking
    f.seek(10)     # Jump to byte 10
    position = f.tell()  # Get current position
    f.seek(0, 2)   # Jump to end of file
```

This is particularly useful when working with binary files or implementing file-based databases.

## Practical Considerations

**Encoding matters**. Always specify `encoding='utf-8'` unless you have a specific reason not to. This prevents encoding issues across different systems.

**Error handling** should wrap file operations since files might not exist, permissions might be wrong, or disk space might be full.

**Performance considerations**: Reading large files line by line is more memory-efficient than loading everything at once. For structured data, consider using specialized libraries like `pandas` for CSV files.

**Security note**: Never use `pickle.load()` on untrusted data - it can execute arbitrary code. Stick with JSON for data exchange unless you specifically need Python object serialization in a controlled environment.

These input/output operations form the foundation of most Python applications. Whether you're building web services, data analysis tools, or system scripts, you'll use these patterns daily.
