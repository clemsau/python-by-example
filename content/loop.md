+++
title = "Loop"
+++

## Loop in Python

The `for` keyword is used to iterate over a sequence of elements. It is the most common way to perform a loop in Python.

```python
nums = [1, 2, 3, 4, 5]
for num in nums:
    print(num) # Output: 1, 2, 3, 4, 5
```

Usually, the `range()` function is used to generate a sequence of numbers to iterate over.

```python
for i in range(5):
    print(i) # Output: 0, 1, 2, 3, 4 - range(5) generates numbers from 0 to 4
```

The `enumerate()` function can be used to get both the index and the value of each element in a sequence.

```python
nums = [1, 2, 3, 4, 5]
for i, num in enumerate(nums):
    print(f"Index: {i}, Value: {num}") # Output: Index: 0, Value: 1, Index: 1, Value: 2, Index: 2, Value: 3, Index: 3, Value: 4, Index: 4, Value: 5
```
