+++
title = "Sets and Tuples"
+++

## Sets and Tuples in Python

### Tuples

Tuples are ordered, immutable collections of elements. They are defined by enclosing elements in parentheses `()`.

```python
# Creating a tuple
my_tuple = (1, 2, 3, 4, 5)
print(my_tuple) # Output: (1, 2, 3, 4, 5)

# Tuples can contain elements of different types
mixed_tuple = (1, "hello", True, 3.14)

# Accessing elements by index
print(my_tuple[0]) # Output: 1

# Tuples are immutable
# my_tuple[0] = 10 # This will raise an error

# Length of a tuple
print(len(my_tuple)) # Output: 5

# Tuple unpacking
a, b, c, d, e = my_tuple
print(a, c, e) # Output: 1 3 5
```

### Sets

Sets are unordered collections of unique elements. They are defined by enclosing elements in curly braces `{}` or by using the `set()` function.

```python
# Creating a set
my_set = {1, 2, 3, 4, 5}
print(my_set) # Output: {1, 2, 3, 4, 5}

# Sets automatically remove duplicates
duplicates = {1, 2, 2, 3, 3, 3}
print(duplicates) # Output: {1, 2, 3}

# Creating a set from a list
list_to_set = set([1, 2, 3, 2, 1])
print(list_to_set) # Output: {1, 2, 3}

# Set operations
set1 = {1, 2, 3}
set2 = {3, 4, 5}

# Union
print(set1 | set2) # Output: {1, 2, 3, 4, 5}

# Intersection
print(set1 & set2) # Output: {3}

# Difference
print(set1 - set2) # Output: {1, 2}

# Adding elements
my_set.add(6)
print(my_set) # Output: {1, 2, 3, 4, 5, 6}

# Removing elements
my_set.remove(6)
print(my_set) # Output: {1, 2, 3, 4, 5}
```
