+++
title = "Formatting"
+++

## Formatting in Python

Formatting strings in python is very convenient, mostly because most types have a `__str__` method that returns a string representation of the object. Because of this, we can format most types seamlessly.

The most common way to format strings in Python is by using the `format` method. This method allows you to insert values into a string by using placeholders and passing the values as arguments to the `format` method.

By using the `format` method, you can insert values into a string in a specific order defined by the placeholders `{}`.

```python
name = "Alice"
age = 30

message = "Hello, my name is {} and I am {} years old.".format(name, age)
print(message) # Output: Hello, my name is Alice and I am 30 years old.
```

From python 3.6 onwards, you can also use f-strings to format strings. F-strings Let you embed expressions inside string literals, using curly braces `{}`.

```python
name = "Alice"
age = 30

message = f"Hello, my name is {name} and I am {age} years old."
print(message) # Output: Hello, my name is Alice and I am 30 years old.
```
