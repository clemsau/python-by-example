+++
title = "Static Typing"
+++

## Static Typing in Python

Python is dynamically typed by default, but it supports optional static type hints through type annotations.

Type hints don't affect runtime behavior but help with code documentation, IDE support, and static type checking tools like mypy.

It is highly recommended to use type hints in your code for better readability and maintainability.

```python
# Basic type annotations
name: str = "Alice"
age: int = 30
height: float = 1.75
is_student: bool = True
```

Function parameters and return types can also be annotated:

```python
def greet(name: str) -> str:
    return f"Hello, {name}!"

# Function with multiple typed parameters
def calculate_bmi(weight: float, height: float) -> float:
    return weight / (height ** 2)
```

For more complex types, you can use the `typing` module:

```python
from typing import List, Dict, Tuple, Optional, Union

# List of integers
numbers: List[int] = [1, 2, 3, 4, 5]

# Dictionary with string keys and integer values
scores: Dict[str, int] = {"Alice": 95, "Bob": 87}

# Tuple with specific types for each position
person: Tuple[str, int, float] = ("Alice", 30, 1.75)

# Optional type (can be the specified type or None)
middle_name: Optional[str] = None

# Union type (can be any of the specified types)
id_number: Union[int, str] = "A12345"
```

Type checking can be performed using tools like mypy:

```bash
# Install mypy
pip install mypy

# Run mypy on your Python file
mypy your_file.py
```

This will check for type errors and provide feedback on your code's type annotations.
