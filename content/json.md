+++
title = "JSON"
+++

## JSON in Python

Python provides the `json` module to work with JSON data.

### Encoding (Python to JSON)

Converting Python objects to JSON strings is called encoding, or serializing, or marshaling. The `json` module provides two main functions for this: `json.dumps()` which converts a Python object to a JSON string, and `json.dump()` which writes JSON data to a file.

```python
import json

# Python dictionary
data = {
    "name": "Alice",
    "age": 30,
    "is_student": False,
    "courses": ["Python", "Data Science", "Web Development"],
    "address": {
        "city": "New York",
        "country": "USA"
    }
}

# Convert Python object to JSON string
json_string = json.dumps(data)
print(json_string)
# Output: {"name": "Alice", "age": 30, "is_student": false, "courses": ["Python", "Data Science", "Web Development"], "address": {"city": "New York", "country": "USA"}}

# Pretty-print with indentation
pretty_json = json.dumps(data, indent=4)
print(pretty_json)
# Output:
# {
#     "name": "Alice",
#     "age": 30,
#     "is_student": false,
#     "courses": [
#         "Python",
#         "Data Science",
#         "Web Development"
#     ],
#     "address": {
#         "city": "New York",
#         "country": "USA"
#     }
# }

# Write JSON to a file
with open('data.json', 'w') as file:
    json.dump(data, file, indent=4)
```

### Decoding (JSON to Python)

Converting JSON strings to Python objects is called decoding, or deserializing, or unmarshaling. The `json` module provides two main functions for this: `json.loads()` which converts a JSON string to a Python object, and `json.load()` which reads JSON data from a file.

```python
import json

# JSON string
json_string = '{"name": "Bob", "age": 25, "is_student": true, "grades": [90, 85, 88]}'

# Convert JSON string to Python object
python_data = json.loads(json_string)
print(python_data)
# Output: {'name': 'Bob', 'age': 25, 'is_student': True, 'grades': [90, 85, 88]}

# Access the data
print(python_data["name"])      # Output: Bob
print(python_data["grades"][0]) # Output: 90

# Read JSON from a file
with open('data.json', 'r') as file:
    file_data = json.load(file)
    print(file_data)
```
