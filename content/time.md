+++
title = "Time"
+++

## Time in Python

Python provides several modules for working with dates and times. The most commonly used are `time` and `datetime`.

### The `time` Module

The `time` module provides functions for working with time-related operations:

```python
import time

# Get current timestamp in seconds since the epoch (January 1, 1970)
current_time = time.time()
print(current_time)  # Output: 1716316800.1234 (example value)

# Sleep for a specified number of seconds
time.sleep(1)  # Pause execution for 1 second

# Get formatted time
local_time = time.localtime()
formatted_time = time.strftime("%Y-%m-%d %H:%M:%S", local_time)
print(formatted_time)  # Output: 2025-05-21 14:30:00 (example)
```

### The `datetime` Module

The `datetime` module provides classes for manipulating dates and times.

You would want to use is over the time modul in the case you need to work with dates and times in a more human-readable format, instead of just a timestamp.

```python
from datetime import datetime, timedelta

# Get current date and time
now = datetime.now()
print(now)  # Output: 2025-05-21 14:30:00.123456 (example)

# Create a specific date and time
specific_date = datetime(2025, 5, 21, 14, 30)
print(specific_date)  # Output: 2025-05-21 14:30:00

# Format a datetime
formatted = now.strftime("%Y-%m-%d %H:%M:%S")
print(formatted)  # Output: 2025-05-21 14:30:00

# Parse a string into a datetime
date_string = "2025-05-21 14:30:00"
parsed_date = datetime.strptime(date_string, "%Y-%m-%d %H:%M:%S")
print(parsed_date)  # Output: 2025-05-21 14:30:00
```

### Time Arithmetic

You can perform arithmetic operations with `timedelta`:

```python
from datetime import datetime, timedelta

now = datetime.now()

# Add 1 day
tomorrow = now + timedelta(days=1)
print(tomorrow)

# Subtract 1 hour
one_hour_ago = now - timedelta(hours=1)
print(one_hour_ago)

# Calculate difference between two datetimes
future_date = datetime(2025, 12, 31)
time_difference = future_date - now
print(f"Days until New Year: {time_difference.days}")
```

### Time Comparison

Datetime objects can be easily compared using standard comparison operators:

```python
from datetime import datetime

date1 = datetime(2025, 5, 21, 14, 30)
date2 = datetime(2025, 5, 21, 15, 45)
date3 = datetime(2025, 5, 21, 14, 30)

# Check if one time is later than another
print(date2 > date1)  # Output: True

# Check if times are equal
print(date1 == date3)  # Output: True

# Check if time is earlier
print(date1 < date2)  # Output: True

# Find the earliest/latest time
dates = [date2, date1, date3]
earliest = min(dates)
latest = max(dates)
print(f"Earliest: {earliest}")  # Output: Earliest: 2025-05-21 14:30:00
print(f"Latest: {latest}")      # Output: Latest: 2025-05-21 15:45:00
```
