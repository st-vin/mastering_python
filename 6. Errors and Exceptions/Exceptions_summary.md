# Python Error Handling

## The Two Types of Errors You'll See

**Syntax Errors** are the basic mistakes - missing colons, wrong indentation, typos. These stop your code from even running. The parser points right to where it thinks the problem is, though sometimes you need to look just before that spot.

**Exceptions** happen when your code is syntactically correct but something goes wrong during execution. These are the ones you'll spend time handling.

## Common Exceptions You'll Handle Daily

The big three you'll see constantly:
- **TypeError** - mixing incompatible types like trying to add a string and number
- **NameError** - using a variable that doesn't exist 
- **ZeroDivisionError** - dividing by zero

Others that come up regularly:
- **ValueError** - right type, wrong value (like int("hello"))
- **KeyError** - accessing a dictionary key that doesn't exist
- **IndexError** - list index out of range
- **FileNotFoundError** - trying to open a file that isn't there

## The try/except Pattern

This is your bread and butter for handling errors:

```python
try:
    # risky code here
    x = int(input("Enter a number: "))
except ValueError:
    # handle the specific error
    print("That wasn't a number")
```

You can catch multiple exceptions:
```python
except (ValueError, TypeError):
    # handles both types
```

Or handle them differently:
```python
try:
    # some code
except ValueError:
    # handle value errors
except TypeError:
    # handle type errors
except Exception as e:
    # catch anything else
    print(f"Unexpected error: {e}")
```

## The Complete try Block Structure

```python
try:
    # main code
except SpecificError:
    # handle specific errors
else:
    # runs only if no exception occurred
finally:
    # always runs, good for cleanup
```

The **else** clause runs when nothing goes wrong - useful for code that should only run on success.

The **finally** clause always runs, whether there's an error or not. Perfect for cleanup like closing files or database connections.

## Exception Details and Debugging

When you catch an exception, you can access its details:
```python
try:
    # risky code
except Exception as e:
    print(type(e))      # the exception type
    print(e.args)       # the arguments passed to the exception
    print(str(e))       # the error message
```

This information is crucial for debugging and logging.

## Raising Your Own Exceptions

Sometimes you need to trigger exceptions yourself:
```python
if age < 0:
    raise ValueError("Age cannot be negative")
```

You can re-raise caught exceptions:
```python
try:
    # some code
except ValueError:
    print("Logging the error...")
    raise  # re-raises the same exception
```

## Exception Chaining

When handling one exception leads to another, Python shows you the chain:
```python
try:
    open("missing_file.txt")
except FileNotFoundError:
    raise RuntimeError("Database initialization failed")
```

This creates a chain showing both the original FileNotFoundError and the new RuntimeError.

## The with Statement for Cleanup

Instead of manually managing resources with try/finally, use context managers:
```python
# Old way - manual cleanup
try:
    f = open("file.txt")
    # do something
finally:
    f.close()

# Better way - automatic cleanup
with open("file.txt") as f:
    # do something
    # file automatically closes
```

## Custom Exceptions

For your own applications, create specific exception types:
```python
class DatabaseError(Exception):
    pass

class ValidationError(Exception):
    def __init__(self, field, message):
        self.field = field
        self.message = message
        super().__init__(f"{field}: {message}")
```

## Exception Groups (Python 3.11+)

For handling multiple related exceptions, especially in concurrent code:
```python
def validate_data(items):
    errors = []
    for item in items:
        try:
            validate_item(item)
        except ValidationError as e:
            errors.append(e)
    
    if errors:
        raise ExceptionGroup("Validation failed", errors)
```

Handle them with `except*`:
```python
try:
    validate_data(items)
except* ValidationError:
    print("Some items failed validation")
```

## Adding Context with Notes

You can add additional information to exceptions:
```python
try:
    process_user_data(user_id)
except Exception as e:
    e.add_note(f"Failed for user {user_id}")
    e.add_note(f"At {datetime.now()}")
    raise
```

## Error Handling Patterns: The Four Types

Understanding when and how to handle errors becomes clearer when you classify them by origin and recoverability:

### Type 1: New Recoverable Errors
When your code detects a problem but can fix it without raising an exception:
```python
def add_song_to_database(song):
    if song.year is None:
        song.year = 'Unknown'  # recover silently
    # continue processing
```

### Type 2: Bubbled-Up Recoverable Errors  
When a function you called raised an error, but you know how to handle it:
```python
def add_song_to_database(song):
    try:
        artist = get_artist_from_database(song.artist)
    except NotFound:
        # recover by creating the missing artist
        artist = add_artist_to_database(song.artist)
```

### Type 3: New Non-Recoverable Errors
When your code finds a problem it can't fix - raise an exception to let higher-level code handle it:
```python
def add_song_to_database(song):
    if song.name is None:
        raise ValueError('The song must have a name')
```

### Type 4: Bubbled-Up Non-Recoverable Errors
The most important pattern - when a function you called raises an error you can't handle, **do nothing**:
```python
def new_song():
    song = get_song_from_user()  # might raise KeyboardInterrupt
    add_song_to_database(song)   # might raise DatabaseError
    # Don't catch these - let them bubble up to code that can handle them
```

This isn't ignoring errors - it's letting them reach the right level to be handled properly.

## LBYL vs EAFP Philosophies

**Look Before You Leap (LBYL)** - check conditions first:
```python
if os.path.exists(file_path):
    os.remove(file_path)
```
Problems: race conditions, hard to check all failure modes.

**Easier to Ask Forgiveness than Permission (EAFP)** - try first, handle errors:
```python
try:
    os.remove(file_path)
except OSError as error:
    print(f"Error deleting file: {error}")
```
Generally preferred in Python - more robust and handles all error cases.

## Top-Level Exception Handling

Every application should have a catch-all at the highest level to prevent crashes:
```python
# Command line app
if __name__ == '__main__':
    try:
        my_cli()
    except Exception as error:
        print(f"Unexpected error: {error}")
        sys.exit(1)

# Web framework (Flask does this automatically)
# GUI framework (Tkinter does this automatically)
```

This is the **only** place where catching all exceptions is acceptable.

## Development vs Production Error Handling

Handle errors differently based on environment:
```python
mode = os.environ.get("APP_MODE", "production")

if __name__ == '__main__':
    try:
        my_cli()
    except Exception as error:
        if mode == "development":
            raise  # let it crash for debugging
        else:
            print(f"Unexpected error: {error}")
            sys.exit(1)
```

## When NOT to Handle Exceptions

Many functions should let exceptions bubble up rather than trying to handle them:
```python
# Good - simple, clean, lets errors bubble up
@app.route('/songs/<id>', methods=['PUT'])
def update_song(id):
    db.session.add(song)
    db.session.commit()
    return '', 204

# Bad - handling errors that can't be recovered from
@app.route('/songs/<id>', methods=['PUT'])  
def update_song(id):
    try:
        db.session.add(song)
        db.session.commit()
    except SQLAlchemyError as e:
        # This function can't recover from DB errors
        logger.error('Database error: %s', e)
        return 'Internal Server Error', 500
```

Frameworks like Flask already handle database errors, log them properly, and return appropriate HTTP responses.

## Best Practices for Daily Development

**Be specific** - catch specific exceptions rather than using bare `except:` or catching `Exception` unless you really need to.

**Let errors bubble up** - most functions shouldn't catch exceptions they can't recover from.

**Use EAFP over LBYL** - try the operation and handle errors rather than checking conditions first.

**Fail fast** - validate inputs early and raise exceptions when something is clearly wrong.

**Chain exceptions** - when transforming errors, use `raise NewError() from original_error` to preserve the chain of causation.

**One catch-all per application** - only at the top level to prevent crashes.

**Different behavior for dev/prod** - crash in development for debugging, handle gracefully in production.

**Use logger.exception()** - when logging errors, this includes the full stack trace automatically.

The key insight is that exceptions are a communication mechanism between different layers of your application. Most code should either recover from errors immediately or let them bubble up to code that has the context to handle them properly.