+++
title = "CSV"
+++

## CSV in Python

Python provides the `csv` module to work with CSV files easily.

### Reading CSV Files

The most basic way to read a CSV file is with the `csv.reader` function, which returns an iterable that provides each row as a list of strings.

```python
import csv

# Reading a CSV file
with open('data.csv', 'r', newline='') as file:
    # Create a CSV reader
    csv_reader = csv.reader(file)
    
    # Read the header
    headers = next(csv_reader)
    print(f"Headers: {headers}")
    
    # Read the data rows
    for row in csv_reader:
        print(row)
```

### Reading CSV as Dictionary

When you want to access data by column names rather than indices, the `csv.DictReader` class is more convenient. It returns each row as a dictionary where the keys are taken from the header row.

```python
import csv

# Reading CSV as dictionary (using column names as keys)
with open('data.csv', 'r', newline='') as file:
    csv_reader = csv.DictReader(file)
    
    for row in csv_reader:
        # Access values by column name
        print(f"Name: {row['name']}, Age: {row['age']}")
```

### Writing CSV Files

To create new CSV files, you can use the `csv.writer` class. This allows you to write rows of data to the file, either one at a time or multiple rows at once.

```python
import csv

# Sample data
data = [
    ['name', 'age', 'city'],
    ['Alice', '30', 'New York'],
    ['Bob', '25', 'Los Angeles'],
    ['Charlie', '35', 'Chicago']
]

# Writing to a CSV file
with open('output.csv', 'w', newline='') as file:
    csv_writer = csv.writer(file)
    
    # Write multiple rows at once
    csv_writer.writerows(data)
    
    # Or write one row at a time
    # for row in data:
    #     csv_writer.writerow(row)
```

### Writing Dictionary to CSV

If your data is organized as dictionaries, you can use the `csv.DictWriter` class to write it to a CSV file. This is particularly useful when you already have data in a dictionary format or when working with JSON data.

```python
import csv

# Sample data as list of dictionaries
data = [
    {'name': 'Alice', 'age': '30', 'city': 'New York'},
    {'name': 'Bob', 'age': '25', 'city': 'Los Angeles'},
    {'name': 'Charlie', 'age': '35', 'city': 'Chicago'}
]

# Writing dictionary to CSV file
with open('dict_output.csv', 'w', newline='') as file:
    # Define column names (fieldnames)
    fieldnames = ['name', 'age', 'city']
    
    # Create DictWriter
    writer = csv.DictWriter(file, fieldnames=fieldnames)
    
    # Write header
    writer.writeheader()
    
    # Write data rows
    writer.writerows(data)
```

### CSV Dialect Options

CSV files may use different delimiters, quote characters, or other formatting options. Python allows you to customize these settings by defining a CSV dialect, which lets you work with various CSV formats.

```python
import csv

# Custom CSV dialect
csv.register_dialect('custom',
    delimiter=';',      # Use semicolon as separator
    quotechar='"',      # Quote character
    doublequote=True,   # Double quotes are escaped by doubling them
    skipinitialspace=True,  # Skip spaces after delimiter
    lineterminator='\n',    # Line break character
    quoting=csv.QUOTE_MINIMAL  # Quote only when necessary
)

# Use custom dialect
with open('custom.csv', 'w', newline='') as file:
    writer = csv.writer(file, dialect='custom')
    writer.writerow(['name', 'age', 'city'])
    writer.writerow(['Alice', '30', 'New York'])
```
