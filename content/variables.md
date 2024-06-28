+++
title = "Variables"
+++

## Variables in Python

Variables are explicitly declared and dynamically typed in Python. There is no way to declare the variable, they are created when a value is assigned to them.

```python
foo = 42
bar = "Hello, World!"
```

Because python's variables are dynamically typed, their type can change at any time.

```python
foo = 42
foo = "Hello, World!" # foo is now a string
```

To check the type of a variable, we can use the `type()` function.

```python
foo = 42
print(type(foo)) # Output: <class 'int'>
```

There are no ways to declare constants in Python, so the best practice to simulate a constant is to use a variable and use an uppercase naming as stated in [constant](https://peps.python.org/pep-0008/#constants) section of [PEP8](https://realpython.com/python-pep8/).

```python
PI = 3.14159
```
