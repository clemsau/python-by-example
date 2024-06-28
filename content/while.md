+++
title = "While"
+++

## While in Python

The `while` keyword is used to create a loop that continues to execute as long as a condition is true.

```python
count = 0
while count < 5:
    print(count)
    count += 1
# Output: 0, 1, 2, 3, 4
```

The `break` keyword can be used to exit the loop prematurely.

The `continue` keyword can be used to skip the rest of the code block and continue with the next iteration of the loop.

```python
count = 0
while count < 5:
    if count == 0:
        continue

    if count == 3:
        break
    
    print(count)
    count += 1
# Output: 0, 2
```
