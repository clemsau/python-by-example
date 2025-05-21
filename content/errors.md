+++
title = "Errors"
+++

## Error Handling in Python

In Python, errors are handled using try-except blocks. When an error occurs, Python raises an exception which can be caught and processed.

### Basic Try-Except

The `try` block contains code that might cause an exception, and the `except` block contains code to handle the exception.

```python
try:
    x = 10 / 0  # Division by zero causes an error
except:
    print("An error occurred")  # Output: An error occurred
```

### Catching Specific Exceptions

You can catch specific exceptions by specifying the exception type.

```python
try:
    x = 10 / 0
except ZeroDivisionError:
    print("Division by zero")  # Output: Division by zero
except ValueError:
    print("Invalid value")
```

### Accessing Exception Information

You can access the exception information using the `as` keyword.

```python
try:
    x = 10 / 0
except ZeroDivisionError as error:
    print(f"Error message: {error}")  # Output: Error message: division by zero
```

### Finally Block

The `finally` block is executed regardless of whether an exception occurred or not.

```python
try:
    x = 10 / 2
    print(x)  # Output: 5.0
except ZeroDivisionError:
    print("Division by zero")
finally:
    print("This always executes")  # Output: This always executes
```

### Else Block

The `else` block is executed only if no exceptions occur in the try block.

```python
try:
    x = 10 / 5
except ZeroDivisionError:
    print("Division by zero")
else:
    print(f"Result is {x}")  # Output: Result is 2.0
```

### Raising Exceptions

You can raise exceptions using the `raise` keyword.

```python
x = -5
if x < 0:
    raise ValueError("x cannot be negative")  # Raises: ValueError: x cannot be negative
```

### Common Built-in Exceptions

Python has many built-in exceptions such as:

- `ValueError`: Raised when a function receives an argument of correct type but invalid value
- `TypeError`: Raised when an operation is performed on an inappropriate type
- `IndexError`: Raised when trying to access an index that is out of range
- `KeyError`: Raised when a dictionary key is not found
- `FileNotFoundError`: Raised when trying to access a file that does not exist
