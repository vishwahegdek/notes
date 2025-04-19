# Python Cheatsheet: Basics to Intermediate

## Table of Contents
- [Python Basics](#python-basics)
  - [Variables and Data Types](#variables-and-data-types)
  - [Operators](#operators)
  - [Control Flow](#control-flow)
  - [Functions](#functions)
  - [Error Handling](#error-handling)
- [Data Structures](#data-structures)
  - [Lists](#lists)
  - [Tuples](#tuples)
  - [Dictionaries](#dictionaries)
  - [Sets](#sets)
  - [Strings](#strings)
- [Algorithms](#algorithms)
  - [Searching](#searching)
  - [Sorting](#sorting)
  - [Recursion](#recursion)
- [Time & Space Complexity](#time--space-complexity)
- [Python Standard Library Highlights](#python-standard-library-highlights)
- [Common Idioms and Tricks](#common-idioms-and-tricks)

## Python Basics

### Variables and Data Types

```python
# Variables (no type declaration needed)
x = 5           # Integer
y = 3.14        # Float
name = "Python" # String
is_valid = True # Boolean

# Multiple assignment
a, b, c = 1, 2, 3

# Type conversion
str_num = "42"
num = int(str_num)  # 42
float_num = float(str_num)  # 42.0
str_val = str(num)  # "42"

# Type checking
type(x)  # <class 'int'>
isinstance(x, int)  # True

# Constants (by convention, uppercase)
PI = 3.14159
MAX_SIZE = 100
```

### Operators

```python
# Arithmetic
a + b    # Addition
a - b    # Subtraction
a * b    # Multiplication
a / b    # Division (returns float)
a // b   # Floor division
a % b    # Modulus (remainder)
a ** b   # Exponentiation (a to the power of b)

# Assignment
x = 5
x += 3   # x = x + 3
x -= 2   # x = x - 2
x *= 2   # x = x * 2
x /= 4   # x = x / 4
x //= 2  # x = x // 2
x %= 3   # x = x % 3
x **= 2  # x = x ** 2

# Comparison
a == b   # Equal to
a != b   # Not equal to
a > b    # Greater than
a < b    # Less than
a >= b   # Greater than or equal to
a <= b   # Less than or equal to

# Logical
x and y  # True if both are true
x or y   # True if at least one is true
not x    # True if x is false

# Identity
x is y     # True if x and y are the same object
x is not y # True if x and y are different objects

# Membership
x in y     # True if x is a member of y
x not in y # True if x is not a member of y
```

### Control Flow

```python
# If-Else statements
if condition:
    # code block
elif another_condition:
    # code block
else:
    # code block

# Ternary operator (conditional expression)
value = x if condition else y

# For loops
for item in iterable:
    # code block

# Range-based for loops
for i in range(5):  # 0, 1, 2, 3, 4
    print(i)

for i in range(2, 8):  # 2, 3, 4, 5, 6, 7
    print(i)

for i in range(1, 10, 2):  # 1, 3, 5, 7, 9
    print(i)

# While loops
while condition:
    # code block
    if break_condition:
        break  # Exit the loop
    if skip_condition:
        continue  # Skip to the next iteration

# Loop with else (executed if loop completes without break)
for item in iterable:
    # code block
else:
    # executed if loop completes without break

# List comprehension
squares = [x**2 for x in range(10)]
evens = [x for x in range(20) if x % 2 == 0]

# Dictionary comprehension
square_dict = {x: x**2 for x in range(10)}
```

### Functions

```python
# Basic function
def greet(name):
    return f"Hello, {name}!"

# Default parameters
def greet(name="World"):
    return f"Hello, {name}!"

# Multiple parameters
def add_numbers(a, b):
    return a + b

# Arbitrary number of arguments
def sum_all(*args):
    return sum(args)

# Keyword arguments
def person_info(name, age, city):
    return f"{name} is {age} years old and lives in {city}."

# Call with keyword arguments
person_info(name="Alice", age=30, city="New York")
person_info(age=25, city="Boston", name="Bob")  # Order doesn't matter

# Arbitrary keyword arguments
def user_profile(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")

# Lambda functions (anonymous)
square = lambda x: x**2
add = lambda x, y: x + y

# Docstrings
def multiply(a, b):
    """
    Multiply two numbers and return the result.
    
    Args:
        a: First number
        b: Second number
        
    Returns:
        The product of a and b
    """
    return a * b
```

### Error Handling

```python
# Basic try-except
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero!")

# Multiple exceptions
try:
    num = int("abc")
except ValueError:
    print("Invalid conversion")
except ZeroDivisionError:
    print("Division by zero")

# Catch any exception
try:
    # risky code
except Exception as e:
    print(f"An error occurred: {e}")

# Try-except-else-finally
try:
    num = int("123")
except ValueError:
    print("Invalid conversion")
else:
    # Runs if no exception
    print("Conversion successful")
finally:
    # Always runs
    print("End of try block")

# Raising exceptions
if value < 0:
    raise ValueError("Value cannot be negative")

# Custom exceptions
class CustomError(Exception):
    def __init__(self, message):
        self.message = message
        super().__init__(self.message)
```

## Data Structures

### Lists

```python
# Creation
empty_list = []
numbers = [1, 2, 3, 4, 5]
mixed = [1, "hello", 3.14, True]

# Access elements
first = numbers[0]  # First element
last = numbers[-1]  # Last element

# Slicing
subset = numbers[1:4]  # [2, 3, 4]
beginning = numbers[:3]  # [1, 2, 3]
end = numbers[2:]  # [3, 4, 5]
copy_list = numbers[:]  # Creates a shallow copy

# Common methods
numbers.append(6)         # Add to end: [1, 2, 3, 4, 5, 6]
numbers.insert(2, 2.5)    # Insert at index: [1, 2, 2.5, 3, 4, 5, 6]
numbers.extend([7, 8])    # Add multiple: [1, 2, 2.5, 3, 4, 5, 6, 7, 8]
numbers.remove(2.5)       # Remove first occurrence
popped = numbers.pop()    # Remove and return last item
popped_idx = numbers.pop(1)  # Remove at index
numbers.clear()           # Remove all items

# Finding elements
index = numbers.index(3)  # Find position of value
count = numbers.count(2)  # Count occurrences
is_present = 4 in numbers  # Check membership

# Sorting
numbers.sort()            # Sort in-place
numbers.sort(reverse=True)  # Sort descending
sorted_list = sorted(numbers)  # Returns new sorted list
numbers.reverse()         # Reverse in-place

# List operations
combined = numbers + [10, 11]  # Concatenation
repeated = [0] * 5  # [0, 0, 0, 0, 0]
length = len(numbers)  # Number of elements

# Nested lists (2D)
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
element = matrix[1][2]  # Access 6
```

### Tuples

```python
# Creation (immutable)
empty_tuple = ()
single_item = (1,)  # Note the comma
coordinates = (10, 20)
mixed_tuple = (1, "hello", 3.14)

# Accessing elements (same as lists)
x = coordinates[0]  # 10

# Methods
count = coordinates.count(10)  # Count occurrences
index = mixed_tuple.index("hello")  # Find position

# Tuple operations
combined = coordinates + (30, 40)
repeated = coordinates * 3
length = len(coordinates)

# Tuple unpacking
x, y = coordinates  # x = 10, y = 20
a, *rest, b = (1, 2, 3, 4, 5)  # a = 1, rest = [2, 3, 4], b = 5

# Tuple to list and back
tuple_from_list = tuple([1, 2, 3])
list_from_tuple = list(coordinates)
```

### Dictionaries

```python
# Creation
empty_dict = {}
person = {"name": "Alice", "age": 30, "city": "New York"}
using_dict = dict(name="Bob", age=25, country="USA")

# Accessing elements
name = person["name"]  # Can raise KeyError
age = person.get("age")  # Returns None if key doesn't exist
city = person.get("city", "Unknown")  # Default value if not found

# Adding/Updating
person["email"] = "alice@example.com"  # Add new key-value
person["age"] = 31  # Update existing
person.update({"phone": "123-456-7890", "age": 32})  # Add/update multiple

# Removing
removed = person.pop("email")  # Remove and return value
person.popitem()  # Remove and return last item as tuple
del person["age"]  # Delete specific key
person.clear()  # Remove all items

# Methods
keys = person.keys()  # View of keys
values = person.values()  # View of values
items = person.items()  # View of (key, value) tuples

# Checking keys
has_key = "name" in person  # Check if key exists

# Dictionary comprehension
squares = {x: x**2 for x in range(6)}  # {0:0, 1:1, 2:4, ...}

# Nested dictionaries
employee = {
    "name": "John",
    "position": "Developer",
    "skills": ["Python", "JavaScript"],
    "address": {
        "city": "Boston",
        "state": "MA"
    }
}
```

### Sets

```python
# Creation (unordered, unique elements)
empty_set = set()  # Not {}, which creates an empty dict
numbers = {1, 2, 3, 4, 5}
unique = set([1, 2, 2, 3, 3, 3])  # {1, 2, 3}

# Adding elements
numbers.add(6)  # Add single element
numbers.update({7, 8}, [9, 10])  # Add multiple

# Removing elements
numbers.remove(5)  # Raises KeyError if not found
numbers.discard(5)  # No error if not found
popped = numbers.pop()  # Remove and return arbitrary element
numbers.clear()  # Remove all

# Set operations
a = {1, 2, 3, 4}
b = {3, 4, 5, 6}

union = a | b  # OR: a.union(b) - all elements from both
intersection = a & b  # OR: a.intersection(b) - common elements
difference = a - b  # OR: a.difference(b) - in a but not in b
sym_diff = a ^ b  # OR: a.symmetric_difference(b) - in either but not both

# Checking subsets/supersets
is_subset = a <= b  # OR: a.issubset(b)
is_superset = a >= b  # OR: a.issuperset(b)
is_disjoint = a.isdisjoint({7, 8})  # True if no common elements
```

### Strings

```python
# Creation
s1 = 'Single quotes'
s2 = "Double quotes"
s3 = '''
Multi-line
string
'''

# String methods
s = "hello world"
upper_s = s.upper()  # "HELLO WORLD"
lower_s = s.lower()  # "hello world"
cap_s = s.capitalize()  # "Hello world"
title_s = s.title()  # "Hello World"

# Checking content
is_digit = "123".isdigit()  # True
is_alpha = "abc".isalpha()  # True
is_alnum = "abc123".isalnum()  # True
is_space = "   ".isspace()  # True

# Finding and replacing
pos = s.find("world")  # Returns index or -1
count = s.count("l")  # Count occurrences
new_s = s.replace("world", "Python")  # Replace all occurrences

# Splitting and joining
words = s.split()  # Split by whitespace: ["hello", "world"]
parts = "a,b,c".split(",")  # Split by comma: ["a", "b", "c"]
joined = ", ".join(["apple", "banana", "cherry"])  # "apple, banana, cherry"

# Stripping whitespace
trimmed = "  spaces  ".strip()  # "spaces"
left_trim = "  spaces  ".lstrip()  # "spaces  "
right_trim = "  spaces  ".rstrip()  # "  spaces"

# Formatting
name = "Alice"
age = 30
# f-strings (Python 3.6+)
intro = f"I'm {name} and I'm {age} years old"
# format() method
intro = "I'm {} and I'm {} years old".format(name, age)
# Named placeholders
intro = "I'm {name} and I'm {age} years old".format(name=name, age=age)

# String operations
combined = "hello" + " " + "world"  # Concatenation
repeated = "abc" * 3  # "abcabcabc"
length = len(s)  # String length
```

## Algorithms

### Searching

```python
# Linear Search
def linear_search(arr, target):
    for i, item in enumerate(arr):
        if item == target:
            return i  # Return index if found
    return -1  # Return -1 if not found

# Binary Search (on sorted array)
def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    
    while left <= right:
        mid = (left + right) // 2
        
        if arr[mid] == target:
            return mid  # Found
        elif arr[mid] < target:
            left = mid + 1  # Search right half
        else:
            right = mid - 1  # Search left half
            
    return -1  # Not found

# Binary Search (recursive)
def binary_search_recursive(arr, target, left, right):
    if left > right:
        return -1  # Not found
        
    mid = (left + right) // 2
    
    if arr[mid] == target:
        return mid  # Found
    elif arr[mid] < target:
        return binary_search_recursive(arr, target, mid + 1, right)
    else:
        return binary_search_recursive(arr, target, left, mid - 1)
```

### Sorting

```python
# Bubble Sort
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        swapped = False
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]  # Swap
                swapped = True
        if not swapped:
            break  # Array is sorted
    return arr

# Selection Sort
def selection_sort(arr):
    n = len(arr)
    for i in range(n):
        min_idx = i
        for j in range(i + 1, n):
            if arr[j] < arr[min_idx]:
                min_idx = j
        arr[i], arr[min_idx] = arr[min_idx], arr[i]  # Swap
    return arr

# Insertion Sort
def insertion_sort(arr):
    for i in range(1, len(arr)):
        key = arr[i]
        j = i - 1
        while j >= 0 and arr[j] > key:
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = key
    return arr

# Merge Sort
def merge_sort(arr):
    if len(arr) <= 1:
        return arr
        
    mid = len(arr) // 2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])
    
    return merge(left, right)

def merge(left, right):
    result = []
    i = j = 0
    
    while i < len(left) and j < len(right):
        if left[i] <= right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1
    
    result.extend(left[i:])
    result.extend(right[j:])
    return result

# Quick Sort
def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    
    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    
    return quick_sort(left) + middle + quick_sort(right)

# Using Python's built-in sort
sorted_list = sorted(my_list)  # Returns new sorted list
my_list.sort()  # Sorts in-place

# Sorting with custom key
names = ["alice", "Bob", "david", "Charlie"]
sorted_names = sorted(names, key=str.lower)  # Case-insensitive sort
```

### Recursion

```python
# Factorial
def factorial(n):
    if n == 0 or n == 1:
        return 1
    else:
        return n * factorial(n - 1)

# Fibonacci sequence
def fibonacci(n):
    if n <= 1:
        return n
    else:
        return fibonacci(n-1) + fibonacci(n-2)

# Improved Fibonacci with memoization
def fibonacci_memo(n, memo={}):
    if n in memo:
        return memo[n]
    if n <= 1:
        return n
    memo[n] = fibonacci_memo(n-1, memo) + fibonacci_memo(n-2, memo)
    return memo[n]

# Sum of array elements
def sum_array(arr):
    if not arr:
        return 0
    return arr[0] + sum_array(arr[1:])

# Greatest common divisor (GCD)
def gcd(a, b):
    if b == 0:
        return a
    return gcd(b, a % b)
```

## Time & Space Complexity

```
Common Time Complexities:
- O(1): Constant time - Direct access (array indexing, hash table lookup)
- O(log n): Logarithmic - Binary search, balanced trees
- O(n): Linear - Linear search, traversing an array
- O(n log n): Linearithmic - Merge sort, quick sort (average)
- O(n²): Quadratic - Bubble sort, selection sort, insertion sort
- O(2^n): Exponential - Recursive algorithms without memoization
- O(n!): Factorial - Generating all permutations

Common Space Complexities:
- O(1): Constant - Fixed number of variables
- O(n): Linear - Data proportional to input size
- O(n²): Quadratic - 2D arrays/matrices

Algorithm complexities:
- Sorting:
  - Quick sort: O(n log n) average, O(n²) worst case
  - Merge sort: O(n log n)
  - Heap sort: O(n log n)
  - Bubble/Selection/Insertion sort: O(n²)
  
- Searching:
  - Linear search: O(n)
  - Binary search: O(log n)
  - Hash table lookup: O(1) average
```

## Python Standard Library Highlights

```python
# Math operations
import math
math.sqrt(16)      # Square root: 4.0
math.factorial(5)  # Factorial: 120
math.pi            # Pi constant
math.ceil(4.2)     # Ceiling: 5
math.floor(4.8)    # Floor: 4
math.gcd(8, 12)    # Greatest common divisor: 4

# Random numbers
import random
random.random()        # Float between 0 and 1
random.randint(1, 10)  # Integer between 1 and 10
random.choice([1, 2, 3, 4])  # Random item from list
random.shuffle(my_list)  # Shuffle list in-place
random.sample(range(100), 10)  # 10 unique random numbers

# Date and time
import datetime
now = datetime.datetime.now()  # Current date and time
today = datetime.date.today()  # Current date
time_delta = datetime.timedelta(days=7)  # Time period
future = now + time_delta  # Date arithmetic
formatted = now.strftime("%Y-%m-%d %H:%M:%S")  # Format date

# File handling
# Read file
with open("file.txt", "r") as f:
    content = f.read()  # Read entire file
    # OR
    lines = f.readlines()  # Read into list of lines
    # OR
    for line in f:  # Read line by line
        print(line.strip())

# Write file
with open("output.txt", "w") as f:
    f.write("Hello World\n")
    f.writelines(["Line 1\n", "Line 2\n"])

# JSON handling
import json
# Parse JSON string
data = json.loads('{"name": "John", "age": 30}')
# Convert Python object to JSON string
json_str = json.dumps(data, indent=4)
# Read JSON file
with open("data.json", "r") as f:
    data = json.load(f)
# Write JSON file
with open("output.json", "w") as f:
    json.dump(data, f, indent=4)

# Regular expressions
import re
pattern = r"\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}\b"
is_email = re.match(pattern, "user@example.com")
found = re.search(r"world", "hello world")  # Find first match
all_matches = re.findall(r"\d+", "There are 3 apples and 5 oranges")
replaced = re.sub(r"\bworld\b", "Python", "hello world")  # Replace
```

## Common Idioms and Tricks

```python
# Swap values
a, b = b, a

# Check if value is one of multiple values
if x in [1, 2, 3, 4]:
    # Do something

# Create a dict from two lists
names = ["Alice", "Bob", "Charlie"]
ages = [25, 30, 35]
name_to_age = dict(zip(names, ages))

# Flatten a list of lists
nested = [[1, 2], [3, 4], [5, 6]]
flattened = [item for sublist in nested for item in sublist]
# OR
import itertools
flattened = list(itertools.chain.from_iterable(nested))

# Count occurrences in a list
from collections import Counter
count = Counter(["a", "b", "a", "c", "b", "a"])

# Defaultdict to avoid KeyError
from collections import defaultdict
counts = defaultdict(int)  # Default value is 0
for name in ["Alice", "Bob", "Alice", "Charlie"]:
    counts[name] += 1

# Get unique elements while preserving order
unique_items = list(dict.fromkeys(items))

# Sort a list of dictionaries by a key
users = [{"name": "Alice", "age": 25}, {"name": "Bob", "age": 20}]
sorted_by_age = sorted(users, key=lambda x: x["age"])

# Get most frequent item
most_common = max(set(items), key=items.count)

# Reverse a string/list
reversed_str = s[::-1]
reversed_list = items[::-1]

# Use enumerate for index and value
for i, item in enumerate(items):
    print(f"Item {i}: {item}")

# Check if all/any conditions are met
is_all_positive = all(num > 0 for num in numbers)
has_any_even = any(num % 2 == 0 for num in numbers)

# Context manager for managing resources
class MyContext:
    def __enter__(self):
        print("Entering context")
        return self
    
    def __exit__(self, exc_type, exc_val, exc_tb):
        print("Exiting context")

with MyContext() as ctx:
    print("Inside context")
```
