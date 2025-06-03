+++
title = "Logging"
+++

## Logging in Python

Logging is a way to track events that happen when your program runs. It's much better than using `print()` statements because you can control the level of detail and where the log messages go.

### Basic Logging

Python's `logging` module provides a simple way to add logging to your programs:

```python
import logging

logging.debug("This is a debug message")
logging.info("This is an info message")
logging.warning("This is a warning message")
logging.error("This is an error message")
logging.critical("This is a critical message")

# Output (only warning and above are shown by default):
# WARNING:root:This is a warning message
# ERROR:root:This is an error message
# CRITICAL:root:This is a critical message
```

### Setting the Log Level

You can control which messages are displayed by setting the log level:

```python
import logging

# Set the minimum level to INFO
logging.basicConfig(level=logging.INFO)

logging.debug("This won't be shown")
logging.info("This will be shown")
logging.warning("This will be shown")

# Output:
# INFO:root:This will be shown
# WARNING:root:This will be shown
```

### Formatting Log Messages

You can customize how log messages appear:

```python
import logging

logging.basicConfig(
    level=logging.INFO,
    format="%(asctime)s - %(levelname)s - %(message)s"
)

logging.info("Application started")
logging.warning("Low memory warning")

# Output:
# 2024-01-15 10:30:45,123 - INFO - Application started
# 2024-01-15 10:30:45,456 - WARNING - Low memory warning
```

### Logging to a File

Instead of printing to the console, you can save logs to a file:

```python
import logging

logging.basicConfig(
    filename="app.log",
    level=logging.INFO,
    format="%(asctime)s - %(levelname)s - %(message)s"
)

logging.info("User logged in")
logging.error("Database connection failed")

# Messages are saved to app.log file instead of console
```

### Using Loggers

For more control, you can create your own logger:

```python
import logging

# Create a logger
logger = logging.getLogger("my_app")
logger.setLevel(logging.DEBUG)

# Create a console handler
console_handler = logging.StreamHandler()
console_handler.setLevel(logging.INFO)

# Create a formatter
formatter = logging.Formatter("%(name)s - %(levelname)s - %(message)s")
console_handler.setFormatter(formatter)

# Add handler to logger
logger.addHandler(console_handler)

logger.debug("This won't show (below INFO level)")
logger.info("Application initialized")
logger.error("Something went wrong")

# Output:
# my_app - INFO - Application initialized
# my_app - ERROR - Something went wrong
```

### Logging Variables

You can include variables in your log messages:

```python
import logging

logging.basicConfig(level=logging.INFO)

username = "alice"
age = 25

logging.info(f"User {username} logged in, age: {age}")
# Or using % formatting (older style)
logging.info("User %s logged in, age: %d", username, age)

# Output:
# INFO:root:User alice logged in, age: 25
```

### Log Levels Explained

- **DEBUG**: Detailed information for diagnosing problems
- **INFO**: General information about program execution
- **WARNING**: Something unexpected happened, but the program is still working
- **ERROR**: A serious problem occurred, some functionality failed
- **CRITICAL**: A very serious error occurred, the program might stop
