+++
title = "Args and Kwargs"
+++

## Args and Kwargs in Python

`*args` and `**kwargs` allow functions to accept a variable number of arguments. This makes functions more flexible by letting them handle different numbers of parameters.

### *args (Variable Positional Arguments)

`*args` allows a function to accept any number of positional arguments. The arguments are passed as a tuple:

```python
def sum_all(*args):
    total = 0
    for num in args:
        total += num
    return total

print(sum_all(1, 2, 3))        # Output: 6
print(sum_all(1, 2, 3, 4, 5))  # Output: 15
print(sum_all(10))             # Output: 10
```

### **kwargs (Variable Keyword Arguments)

`**kwargs` allows a function to accept any number of keyword arguments. The arguments are passed as a dictionary:

```python
def print_info(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")

print_info(name="Alice", age=30, city="New York")
# Output:
# name: Alice
# age: 30
# city: New York
```

### Combining Regular Parameters with *args and **kwargs

You can mix regular parameters, `*args`, and `**kwargs` in the same function:

```python
def greet(greeting, *names, **options):
    message = greeting
    if names:
        message += " " + ", ".join(names)
    if options.get("excited"):
        message += "!"
    if options.get("uppercase"):
        message = message.upper()
    return message

print(greet("Hello", "Alice", "Bob"))  # Output: Hello Alice, Bob
print(greet("Hi", "Charlie", excited=True))  # Output: Hi Charlie!
print(greet("Hey", uppercase=True))  # Output: HEY
```

### Unpacking Arguments

You can also use `*` and `**` to unpack arguments when calling functions:

```python
def multiply(a, b, c):
    return a * b * c

# Unpacking a list with *
numbers = [2, 3, 4]
result = multiply(*numbers)  # Same as multiply(2, 3, 4)
print(result)  # Output: 24

# Unpacking a dictionary with **
def introduce(name, age, city):
    return f"My name is {name}, I'm {age} years old, and I live in {city}"

person = {"name": "Alice", "age": 25, "city": "Boston"}
print(introduce(**person))  # Output: My name is Alice, I'm 25 years old, and I live in Boston
```

### Practical Examples

#### Function with Default Values and Variable Arguments

```python
def create_user(username, email, *groups, **preferences):
    user = {
        "username": username,
        "email": email,
        "groups": list(groups),
        "preferences": preferences
    }
    return user

user = create_user("alice", "alice@email.com", "admin", "editor", 
                   theme="dark", notifications=True)
print(user)
# Output: {'username': 'alice', 'email': 'alice@email.com', 
#          'groups': ['admin', 'editor'], 
#          'preferences': {'theme': 'dark', 'notifications': True}}
```

#### Wrapper Functions

```python
def log_function_call(func):
    def wrapper(*args, **kwargs):
        print(f"Calling {func.__name__} with args: {args}, kwargs: {kwargs}")
        result = func(*args, **kwargs)
        print(f"Result: {result}")
        return result
    return wrapper

@log_function_call
def add(a, b):
    return a + b

add(3, 5)
# Output:
# Calling add with args: (3, 5), kwargs: {}
# Result: 8
```

#### Flexible Configuration Function

```python
def configure_server(host, port=8000, *middlewares, **settings):
    config = {
        "host": host,
        "port": port,
        "middlewares": list(middlewares),
        "settings": settings
    }
    return config

config = configure_server("localhost", 3000, "auth", "cors", 
                         debug=True, timeout=30)
print(config)
# Output: {'host': 'localhost', 'port': 3000, 
#          'middlewares': ['auth', 'cors'], 
#          'settings': {'debug': True, 'timeout': 30}}
```

### Order Matters

When using all parameter types together, they must be in this specific order:

```python
def example_function(required_arg, default_arg="default", *args, **kwargs):
    print(f"Required: {required_arg}")
    print(f"Default: {default_arg}")
    print(f"Args: {args}")
    print(f"Kwargs: {kwargs}")

example_function("hello", "world", 1, 2, 3, key="value")
# Output:
# Required: hello
# Default: world
# Args: (1, 2, 3)
# Kwargs: {'key': 'value'}
```
