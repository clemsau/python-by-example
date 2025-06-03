+++
title = "Multi-threading"
+++

## Multithreading in Python

Multithreading allows your program to run multiple tasks concurrently. While Python's Global Interpreter Lock (GIL) limits true parallelism for CPU-bound tasks, threading is still useful for I/O-bound operations like file reading, network requests, or waiting for user input.

### Basic Threading

The `threading` module provides tools for creating and managing threads:

```python
import threading
import time

def worker(name):
    print(f"Worker {name} starting")
    time.sleep(2)  # Simulate some work
    print(f"Worker {name} finished")

# Create and start threads
thread1 = threading.Thread(target=worker, args=("A",))
thread2 = threading.Thread(target=worker, args=("B",))

thread1.start()
thread2.start()

# Wait for threads to complete
thread1.join()
thread2.join()

print("All workers finished")

# Output:
# Worker A starting
# Worker B starting
# Worker A finished
# Worker B finished
# All workers finished
```

### Thread with Return Values

Since threads don't return values directly, you can use a list or queue to collect results:

```python
import threading
import time

def calculate_square(number, results, index):
    time.sleep(1)  # Simulate work
    result = number ** 2
    results[index] = result
    print(f"Square of {number} is {result}")

numbers = [2, 3, 4, 5]
results = [None] * len(numbers)
threads = []

# Create threads
for i, num in enumerate(numbers):
    thread = threading.Thread(target=calculate_square, args=(num, results, i))
    threads.append(thread)
    thread.start()

# Wait for all threads to complete
for thread in threads:
    thread.join()

print(f"Results: {results}")
# Output:
# Square of 2 is 4
# Square of 3 is 9
# Square of 4 is 16
# Square of 5 is 25
# Results: [4, 9, 16, 25]
```

### Using ThreadPoolExecutor

The `concurrent.futures` module provides a higher-level interface for threading:

```python
import concurrent.futures
import time

def fetch_data(url):
    print(f"Fetching {url}")
    time.sleep(1)  # Simulate network request
    return f"Data from {url}"

urls = ["site1.com", "site2.com", "site3.com", "site4.com"]

# Use ThreadPoolExecutor
with concurrent.futures.ThreadPoolExecutor(max_workers=2) as executor:
    # Submit all tasks
    future_to_url = {executor.submit(fetch_data, url): url for url in urls}
    
    # Get results as they complete
    for future in concurrent.futures.as_completed(future_to_url):
        url = future_to_url[future]
        try:
            data = future.result()
            print(f"Retrieved: {data}")
        except Exception as e:
            print(f"Error fetching {url}: {e}")

# Output:
# Fetching site1.com
# Fetching site2.com
# Retrieved: Data from site1.com
# Retrieved: Data from site2.com
# Fetching site3.com
# Fetching site4.com
# Retrieved: Data from site3.com
# Retrieved: Data from site4.com
```

### Thread Synchronization with Locks

Use locks to prevent race conditions when multiple threads access shared data:

```python
import threading
import time

# Shared counter
counter = 0
lock = threading.Lock()

def increment_counter(name):
    global counter
    for i in range(5):
        # Acquire lock before modifying shared data
        with lock:
            current = counter
            time.sleep(0.01)  # Simulate some processing
            counter = current + 1
            print(f"Thread {name}: counter = {counter}")

# Create threads
thread1 = threading.Thread(target=increment_counter, args=("A",))
thread2 = threading.Thread(target=increment_counter, args=("B",))

thread1.start()
thread2.start()

thread1.join()
thread2.join()

print(f"Final counter value: {counter}")
# Output shows interleaved but safe increments:
# Thread A: counter = 1
# Thread B: counter = 2
# Thread A: counter = 3
# Thread B: counter = 4
# ...
# Final counter value: 10
```

### Producer-Consumer Pattern with Queue

Use `queue.Queue` for safe communication between threads:

```python
import threading
import queue
import time
import random

def producer(q, name):
    for i in range(5):
        item = f"{name}-item-{i}"
        q.put(item)
        print(f"Producer {name} created {item}")
        time.sleep(random.uniform(0.1, 0.5))
    
def consumer(q, name):
    while True:
        try:
            item = q.get(timeout=2)
            print(f"Consumer {name} processed {item}")
            time.sleep(random.uniform(0.1, 0.3))
            q.task_done()
        except queue.Empty:
            print(f"Consumer {name} timed out")
            break

# Create queue
q = queue.Queue()

# Create threads
producer_thread = threading.Thread(target=producer, args=(q, "P1"))
consumer_thread1 = threading.Thread(target=consumer, args=(q, "C1"))
consumer_thread2 = threading.Thread(target=consumer, args=(q, "C2"))

# Start threads
producer_thread.start()
consumer_thread1.start()
consumer_thread2.start()

# Wait for producer to finish
producer_thread.join()

# Wait for all items to be processed
q.join()

print("All items processed")
```

### Practical Examples

#### Concurrent File Downloads

```python
import threading
import time
import urllib.request

def download_file(url, filename):
    print(f"Starting download: {filename}")
    time.sleep(2)  # Simulate download time
    print(f"Completed download: {filename}")

urls_and_files = [
    ("http://example.com/file1.txt", "file1.txt"),
    ("http://example.com/file2.txt", "file2.txt"),
    ("http://example.com/file3.txt", "file3.txt"),
]

# Download sequentially (slow)
start_time = time.time()
for url, filename in urls_and_files:
    download_file(url, filename)
sequential_time = time.time() - start_time

print(f"Sequential downloads took: {sequential_time:.2f} seconds")

# Download concurrently (faster)
start_time = time.time()
threads = []
for url, filename in urls_and_files:
    thread = threading.Thread(target=download_file, args=(url, filename))
    threads.append(thread)
    thread.start()

for thread in threads:
    thread.join()

concurrent_time = time.time() - start_time
print(f"Concurrent downloads took: {concurrent_time:.2f} seconds")
print(f"Speedup: {sequential_time / concurrent_time:.1f}x")
```

#### Background Task Monitor

```python
import threading
import time

class TaskMonitor:
    def __init__(self):
        self.running = False
        self.thread = None
        
    def start_monitoring(self):
        self.running = True
        self.thread = threading.Thread(target=self._monitor)
        self.thread.start()
        print("Monitoring started")
        
    def stop_monitoring(self):
        self.running = False
        if self.thread:
            self.thread.join()
        print("Monitoring stopped")
        
    def _monitor(self):
        count = 0
        while self.running:
            count += 1
            print(f"Monitor check #{count}")
            time.sleep(1)

# Usage
monitor = TaskMonitor()
monitor.start_monitoring()

# Do some other work
print("Doing main work...")
time.sleep(5)

# Stop monitoring
monitor.stop_monitoring()
```

### Important Notes

1. **GIL Limitation**: Python's Global Interpreter Lock prevents true parallelism for CPU-intensive tasks
2. **Best for I/O-bound tasks**: Threading works well for file operations, network requests, and waiting
3. **Use locks for shared data**: Prevent race conditions when multiple threads modify the same variables
4. **Consider ThreadPoolExecutor**: Higher-level interface that's often easier to use
5. **For CPU-bound tasks**: Consider using `multiprocessing` instead of threading
