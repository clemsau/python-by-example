+++
title = "Decorators"
+++

## Decorators in Python

Decorators are a powerful feature in Python that allow you to modify the behavior of functions or methods without changing their source code. They are applied using the `@decorator_name` syntax above a function definition.

### Basic Decorator

Here's a simple decorator that prints a message before and after a function executes:

```python
def my_decorator(func):
    def wrapper():
        print("Before function call")
        func()
        print("After function call")
    return wrapper

@my_decorator
def say_hello():
    print("Hello!")

say_hello()
# Output:
# Before function call
# Hello!
# After function call
```

Note we use the `wrapper` function to wrap the original function `func`.

### Decorators with Arguments

To create decorators that work with functions that take arguments, the wrapper function should accept `*args` and `**kwargs`:

```python
def my_decorator(func):
    def wrapper(*args, **kwargs):
        print("Before function call")
        result = func(*args, **kwargs)
        print("After function call")
        return result
    return wrapper

@my_decorator
def add(a, b):
    return a + b

print(add(3, 5))
# Output:
# Before function call
# After function call
# 8
```

### Decorators with Parameters

You can also create decorators that accept their own parameters:

```python
def repeat(n):
    def decorator(func):
        def wrapper(*args, **kwargs):
            for _ in range(n):
                result = func(*args, **kwargs)
            return result
        return wrapper
    return decorator

@repeat(3)
def greet(name):
    print(f"Hello, {name}!")

greet("Alice")
# Output:
# Hello, Alice!
# Hello, Alice!
# Hello, Alice!
```

### Practical Examples

Decorators are commonly used for:

#### Timing Functions

```python
import time

def timer(func):
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        print(f"Function {func.__name__} took {time.time() - start:.2f} seconds to run")
        return result
    return wrapper

@timer
def slow_function():
    time.sleep(1)
    
slow_function()
# Output: Function slow_function took 1.00 seconds to run
```

#### Authentication

```python
def require_auth(func):
    def wrapper(user, *args, **kwargs):
        if not user.is_authenticated:
            raise Exception("Authentication required")
        return func(user, *args, **kwargs)
    return wrapper

@require_auth
def view_profile(user):
    return f"Welcome {user.name}!"
```

#### Caching Results

```python
def cache(func):
    stored_results = {}
    
    def wrapper(*args):
        if args in stored_results:
            return stored_results[args]
        result = func(*args)
        stored_results[args] = result
        return result
    
    return wrapper

@cache
def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)

print(fibonacci(35))  # Fast even for large values
```

### Built-in Decorators

Python has several built-in decorators:

```python
# @property turns a method into a property
class Circle:
    def __init__(self, radius):
        self._radius = radius
        
    @property
    def area(self):
        return 3.14 * self._radius ** 2

# @classmethod creates a method that receives the class as the first argument
class MyClass:
    @classmethod
    def from_string(cls, string):
        return cls(string.strip())

# @staticmethod creates a method that doesn't receive the instance or class
class MathUtils:
    @staticmethod
    def add(a, b):
        return a + b
```
