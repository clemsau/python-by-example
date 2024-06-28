+++
title = "Switch"
+++

## Switch in Python

Previously to Python 3.10, there was no built-in switch statement in Python. Switches were implemented using dictionaries or if-elif-else statements.

```python
if case == 'case1':
    print('case1')
elif case == 'case2':
    print('case2')
elif case == 'case3':
    print('case3')
else:
    print('default case')
```

Starting from Python 3.10, the `match` statement was introduced to provide a more concise way to implement switch-case statements.

```python
match case:
    case 'case1':
        print('case1')
    case 'case2':
        print('case2')
    case 'case3':
        print('case3')
    case _:
        print('default case')
```
