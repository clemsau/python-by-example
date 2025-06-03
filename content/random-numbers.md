+++
title = "Random Numbers"
+++

## Random Numbers in Python

Python's `random` module provides functions for generating random numbers and making random choices. This is useful for simulations, games, testing, and many other applications.

### Basic Random Numbers

The `random.random()` function returns a random float between 0.0 and 1.0:

```python
import random

print(random.random())  # Output: 0.8394304074412543 (varies each time)
print(random.random())  # Output: 0.2847192837465829 (different each time)
```

### Random Integers

Use `random.randint()` to generate random integers within a specific range (inclusive):

```python
import random

# Random integer between 1 and 6 (like a dice roll)
dice_roll = random.randint(1, 6)
print(dice_roll)  # Output: 4 (could be any number from 1 to 6)

# Random integer between 10 and 99
number = random.randint(10, 99)
print(number)  # Output: 57 (varies each time)
```

### Random Floats in a Range

Use `random.uniform()` to generate random floats within a specific range:

```python
import random

# Random price between 5.00 and 25.00
price = random.uniform(5.0, 25.0)
print(f"Price: ${price:.2f}")  # Output: Price: $18.73
```

### Random Choices from Lists

Use `random.choice()` to pick a random item from a list:

```python
import random

colors = ["red", "green", "blue", "yellow", "purple"]
random_color = random.choice(colors)
print(random_color)  # Output: blue (varies each time)
```

### Multiple Random Choices

Use `random.choices()` to pick multiple items (with replacement):

```python
import random

numbers = [1, 2, 3, 4, 5]
# Pick 3 random numbers (same number can be picked multiple times)
random_numbers = random.choices(numbers, k=3)
print(random_numbers)  # Output: [2, 5, 2] (varies each time)
```

### Random Sample (No Duplicates)

Use `random.sample()` to pick multiple unique items:

```python
import random

participants = ["Alice", "Bob", "Charlie", "Diana", "Eve"]
# Pick 3 winners (no duplicates)
winners = random.sample(participants, 3)
print(winners)  # Output: ['Charlie', 'Alice', 'Eve'] (varies each time)
```

### Shuffling Lists

Use `random.shuffle()` to randomly rearrange items in a list:

```python
import random

deck = ["A", "2", "3", "4", "5", "6", "7", "8", "9", "10", "J", "Q", "K"]
random.shuffle(deck)
print(deck)  # Output: ['7', 'K', '2', 'A', '9', '3', 'J', '4', '10', '6', '8', 'Q', '5']
```

### Setting a Seed

Use `random.seed()` to make random numbers reproducible (useful for testing):

```python
import random

# Set the seed to get consistent results
random.seed(42)
print(random.randint(1, 100))  # Output: 82 (always the same with seed 42)
print(random.randint(1, 100))  # Output: 15 (always the same sequence)

# Reset seed to get different results
random.seed(42)
print(random.randint(1, 100))  # Output: 82 (same as first call with seed 42)
```
