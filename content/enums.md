+++
title = "Enums"
+++

## Enums in Python

Enumerations (or enums) in Python are a set of symbolic names bound to unique, constant values.

```python
from enum import Enum

# Basic enum definition
class Color(Enum):
    RED = 1
    GREEN = 2
    BLUE = 3

# Accessing enum members
print(Color.RED)       # Output: Color.RED
print(Color.RED.name)  # Output: RED
print(Color.RED.value) # Output: 1
```

Enums can be used for comparison and iteration:

```python
# Comparing enum members
color = Color.RED
if color == Color.RED:
    print("The color is red")  # This will be printed

# Iterating through enum members
for color in Color:
    print(color.name, color.value)
# Output:
# RED 1
# GREEN 2
# BLUE 3
```

For enums where each value must be unique, use `IntEnum` or `unique`:

```python
from enum import IntEnum, unique

# IntEnum forces values to be integers
class Status(IntEnum):
    ERROR = 0
    PENDING = 1
    RUNNING = 2
    SUCCESS = 3

# The @unique decorator ensures no duplicate values
@unique
class UniqueColor(Enum):
    RED = 1
    GREEN = 2
    BLUE = 3
    # DUPLICATE = 1  # This would raise an error
```
