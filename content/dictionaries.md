+++
title = "Dictionaries"
+++

## Dictionaries in Python

In Python, hashmaps are implemented as dictionaries.

They can be declared straightforwardly by using curly brackets `{}` or by using the `dict()` function.

```python
my_dict = {"one": 1, "two": 2, "three": 3}
my_other_dict = dict()
```

Set and Get are done by using a key.

```python
my_dict = {}
my_dict["four"] = 4
print(my_dict["four"]) # Output: 4
```

One dictionary can hold multiple types as key or values.

```python
my_dict = {
    "one": 1, 
    2.5: True, 
    [1, 2]: {"three": 3}
    }
```
