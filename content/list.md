+++
title = "List"
+++

## Lists in Python

In Python, there is no notion of fixed-size arrays. Instead, Python provides a more flexible and powerful data structure called a **list**.

A list is a collection of items that are ordered and changeable. Lists are defined by enclosing the elements in square brackets `[]`.

```python
my_list = [1, 2, 3, 4, 5]
```

A list can contain elements of different data types.

```python
mixed_list = [1, 2.5, "hello", [5, 6, 7]]
```

Lists can be accessed by index, mutable, and can be sliced.

Note that they are zero-indexed, meaning that the first element is at index 0.

```python
my_list = [1, 2, 3, 4, 5]
print(my_list[0]) # Output: 1

my_list[0] = 10
print(my_list) # Output: [10, 2, 3, 4, 5]

print(my_list[1:3]) # Output: [2, 3]
```

Lists can be concatenated using the `+` operator.

```python
list = [1, 2, 3] + [4, 5, 6]
print(list) # Output: [1, 2, 3, 4, 5, 6]
```

We can also use the `*` operator to repeat the elements of a list.

```python
list = [1, 2, 3] * 3
print(list) # Output: [1, 2, 3, 1, 2, 3, 1, 2, 3]
```

To access the length of a list, we can use the `len()` function.

```python
my_list = [1, 2, 3, 4, 5]
print(len(my_list)) # Output: 5
```

To get the last element of a list, we can use negative indexing.

```python
my_list = [1, 2, 3, 4, 5]
print(my_list[-1]) # Output: 5
```

They offer a handful of methods to manipulate the list, such as `append()`, `insert()`, `remove()`, `pop()`, `count()`, `sort()`, and `reverse()`.

```python
my_list = [1, 2, 3, 4, 5]
my_list.append(6)
print(my_list) # Output: [1, 2, 3, 4, 5, 6]

my_list.insert(2, 2.5)
print(my_list) # Output: [1, 2, 2.5, 3, 4, 5, 6]

my_list.remove(2.5)
print(my_list) # Output: [1, 2, 3, 4, 5, 6]

my_list.pop()
print(my_list) # Output: [1, 2, 3, 4, 5]

print(my_list.count(3)) # Output: 1

new_list = [3, 1, 4, 1, 5]
new_list.sort()
print(new_list) # Output: [1, 1, 3, 4, 5]

new_list.reverse()
print(new_list) # Output: [5, 4, 3, 1, 1]
```
