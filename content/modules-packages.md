+++
title = "Modules and Packages"
+++

## Modules and Packages in Python

A module is a Python file containing definitions and statements. Modules are used to organize code into reusable components.

### Importing Modules

To use a module, you need to import it using the `import` statement.

```python
import math
print(math.sqrt(16))  # Output: 4.0
```

You can import specific functions or variables from a module using the `from` keyword.

```python
from math import sqrt
print(sqrt(16))  # Output: 4.0
```

You can also rename imported modules or functions using the `as` keyword.

```python
import math as m
print(m.sqrt(16))  # Output: 4.0

from math import sqrt as square_root
print(square_root(16))  # Output: 4.0
```

### Creating Your Own Modules

To create a module, simply write your Python code in a `.py` file. For example, create a file named `mymodule.py`:

```python
# mymodule.py
def greet(name):
    return f"Hello, {name}!"

PI = 3.14159
```

Then import and use your module:

```python
import mymodule
print(mymodule.greet("Alice"))  # Output: Hello, Alice!
print(mymodule.PI)  # Output: 3.14159
```

### Packages

A package is a collection of modules organized in directories. A package must contain a special file called `__init__.py` (can be empty) to indicate that the directory is a Python package.

```
mypackage/
├── __init__.py
├── module1.py
└── module2.py
```

You can import modules from a package:

```python
import mypackage.module1
mypackage.module1.function()

# Or import specific functions
from mypackage.module2 import function
function()
```

### Standard Library

Python comes with a rich standard library of modules. Some commonly used modules include:

```python
import os  # Operating system interface
import sys  # System-specific parameters and functions
import datetime  # Date and time functions
import json  # JSON encoding and decoding
import random  # Generate random numbers
```
