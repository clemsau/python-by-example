+++
title = "Functions"
+++

## Functions in Python

Like in other programming languages, a function in Python is a block of code that performs a specific task. Functions are defined using the `def` keyword followed by the function name and parentheses `()`. The function body is indented, and it may include a `return` statement to return a value.

```python
def add(a, b):
    return a + b
```

Functions can have parameters and return values. In the example above, the `add` function takes two parameters `a` and `b` and returns their sum.

We can also use default arguments. Default arguments are used when the function is called without passing a value for that argument.

```python
def greet(name="World"):
    return f"Hello, {name}!"
```
