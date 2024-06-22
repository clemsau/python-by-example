+++
title = "Numbers"
+++

## Numbers in Python

In Python, numbers are used to represent numerical data. There are three types of numbers in Python:

- Integers: whole numbers, e.g., 0, 1, 2, 3, etc.
- Floating-point numbers: numbers with a decimal point, e.g., 3.14, 2.718, etc.
- Complex numbers: numbers with a real and imaginary part, e.g., 1 + 2j, 3 - 4j, etc.

Here are some examples of numbers in Python:

```python
# Integer
age = 25
# Floating-point number
pi = 3.14
# Complex number
z = 1 + 2j
```

You can perform arithmetic operations on numbers in Python, such as addition, subtraction, multiplication, and division:

```python
# Addition
sum = 5 + 3
# Subtraction
difference = 5 - 3
# Multiplication
product = 5 * 3
# Division
quotient = 5 / 3
```

As python is a dynamically typed language, you can change the type of a variable at any time, by doing what is called casting.

```python
# Casting an integer to a float
x = 1
y = float(x)
print(y) # Output: 1.0

# Casting a float to an integer
x = 1.9
y = int(x)
print(y) # Output: 1
```

Note that by casting a float to an integer, the decimal part is truncated.
