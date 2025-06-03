+++
title = "Regular Expressions"
+++

## Regular Expressions in Python

Regular expressions (regex) are patterns used to match character combinations in strings. Python's `re` module provides functions for working with regular expressions.

### Basic Pattern Matching

The `re.search()` function searches for a pattern in a string and returns a match object if found:

```python
import re

text = "Hello, my phone number is 123-456-7890"
pattern = r"\d{3}-\d{3}-\d{4}"  # Pattern for phone number

match = re.search(pattern, text)
if match:
    print(match.group())  # Output: 123-456-7890
```

### Finding All Matches

The `re.findall()` function returns all matches as a list:

```python
import re

text = "Contact us at alice@email.com or bob@company.org"
pattern = r"\w+@\w+\.\w+"  # Simple email pattern

emails = re.findall(pattern, text)
print(emails)  # Output: ['alice@email.com', 'bob@company.org']
```

### Common Pattern Characters

Here are the most useful regex characters:

```python
import re

# . matches any character except newline
re.search(r"h.t", "hat")  # Matches "hat"

# * matches zero or more of the preceding character
re.search(r"colou*r", "color")  # Matches "color"

# + matches one or more of the preceding character
re.search(r"go+d", "good")  # Matches "good"

# ? matches zero or one of the preceding character
re.search(r"colou?r", "colour")  # Matches "colour"

# \d matches any digit (0-9)
re.search(r"\d+", "I have 5 apples")  # Matches "5"

# \w matches any word character (letters, digits, underscore)
re.search(r"\w+", "hello_world")  # Matches "hello_world"

# \s matches any whitespace character
re.search(r"\s+", "hello world")  # Matches the space
```

### Character Classes and Ranges

Square brackets define character classes:

```python
import re

# Match vowels
re.findall(r"[aeiou]", "hello world")  # Output: ['e', 'o', 'o']

# Match digits from 1 to 5
re.findall(r"[1-5]", "123456789")  # Output: ['1', '2', '3', '4', '5']

# Match uppercase letters
re.findall(r"[A-Z]", "Hello World")  # Output: ['H', 'W']

# Match anything except digits
re.findall(r"[^\d]", "abc123")  # Output: ['a', 'b', 'c']
```

### Substitution

The `re.sub()` function replaces matches with a replacement string:

```python
import re

text = "The quick brown fox"
# Replace 'fox' with 'dog'
result = re.sub(r"fox", "dog", text)
print(result)  # Output: The quick brown dog

# Remove all digits
text = "abc123def456"
result = re.sub(r"\d", "", text)
print(result)  # Output: abcdef
```

### Groups and Capturing

Parentheses create groups to capture parts of the match:

```python
import re

text = "John Doe was born on 1990-05-15"
pattern = r"(\w+) (\w+) was born on (\d{4})-(\d{2})-(\d{2})"

match = re.search(pattern, text)
if match:
    print(match.group(1))  # Output: John (first name)
    print(match.group(2))  # Output: Doe (last name)
    print(match.group(3))  # Output: 1990 (year)
```

### Practical Examples

#### Validating Email

```python
import re

def is_valid_email(email):
    pattern = r"^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$"
    return bool(re.match(pattern, email))

print(is_valid_email("user@example.com"))  # Output: True
print(is_valid_email("invalid.email"))     # Output: False
```

#### Extracting Numbers from Text

```python
import re

text = "The price is $29.99 and shipping costs $5.50"
numbers = re.findall(r"\d+\.\d+", text)
print(numbers)  # Output: ['29.99', '5.50']
```

#### Cleaning Text

```python
import re

text = "Hello!!!   How are you???   Fine."
# Remove multiple punctuation and extra spaces
cleaned = re.sub(r"[!?]+", "", text)  # Remove multiple ! or ?
cleaned = re.sub(r"\s+", " ", cleaned)  # Replace multiple spaces with single space
print(cleaned.strip())  # Output: Hello How are you Fine.
```
