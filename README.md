# python-interview-questions 
# 1.Difference between list and tuple in python?
# List:
- list is mutable(change,add,remove elements)
- list is created by square brackets []
- performance is slower
# Tuple:
- tuple is immutable(cannot change its contents)
- created by parentheses ()
- tuples rae slightly faster than lists due to immutability

# 2.How do sets help in removing duplicates from a list?

sets do not allow duplicates elements.converting a list to a set removes duplicates automatically.
```python
lst = [5,5,6,7,8,8]
unique = list(set(lst))
print(unique)  # output: [5,6,7,8]
```
# 3.Why are dictionaries faster than lists for lookups?
- Dictionaries use hashing, so lookup is on average O(1) time.
- list lookup is O(n) because it requires a linear search.
  
# 4. How Are Python Strings Immutable if They Allow Operations like replace()?
String methods like replace() return a new string, they don't modify the original string.
```python
s="python"
s1=s.replace("p","j")
print(s)   # "python"
print(s1)  # "jython"
```
# 5.How Do You Merge Two Dictionaries in Python Latest Version?
- the | operator merges the two dictionaries
```python
a = {'e': 1}
b = {'f': 2}
merged = a | b
print(merged)  # {'e': 1, 'f': 2}
```
# 6.Explain Dictionary Comprehension with Example
- dictionary comprehension is a concise and elegant way to create dictionaries in python by using a single line of code
```python
squares = {x: x*x for x in range(5)}
print(squares)  # {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}
```
# 7. What Are Nested Dictionaries and How Do You Access Inner Values?
- A dictionary within a dictionary.
```python
dict = {'std': {'name': 'leo', 'age': 15}}
print(dict['std']['name'])  # Output: leo
```
# 8. How Can You Convert a List of Tuples into a Dictionary?
- dictionary is a collection of key-value pairs
- each tuple must have exactly two elements(key and value)
- the keys must be hashable types(strings,numbers,tuples)

```python
lst = [('red', 1), ('blue', 2)]
d = dict(lst)
print(d)  # {'red': 1, 'blue': 2}
```
# 9. How Would You Handle a Missing Key in a Dictionary?
- Use .get() method:
```python
d = {'a': 1}
print(d.get('b', 'Not found'))  # Output: Not found
```
# 10. Can We Use a List as a Key in a Dictionary? Why/Why Not?
- No, because lists are mutable and unhashable.
-  Only immutable types like tuples can be used as dictionary keys.
  
# 11. What Happens If You Try to Add a Mutable Object to a Set?
- You'll get a TypeError
- since sets require elements to be hashable.
  
```python
s = set()
s.add([1, 2])  # TypeError
```
# 12. Code to Find Common Elements in Two Lists Using Set Operations
```python
a = [1, 2, 3]
b = [2, 3, 4]
common = list(set(a) & set(b))
print(common)  # [2, 3]
```
# 13.Difference Between is and == for String? Syntax?
- is: ideentity operator
 - checks whether two references point to the same object in memory.
 - it returns True only if both variuables point to the exact same object.

- ==: equality operator
  - checks whether two objects have the same value(content) 
```python
a = "python"
b = "python"
print(a == b)  # True
print(a is b)  # True (usually, due to string interning, but not always)
```
# 14.How Does Slicing Work in Tuple and String? Syntax?
- slicing is used to get a subsequence of a sequence.
- Syntax: object[start:stop:step]
- A string is a sequence of characters and immutable, so slicing returns a new string.
- Tuple is an ordered collection of items and immutable, so slicing returns a new tuple.

```python
t = (0, 1, 2, 3, 4)
print(t[1:4])      # (1, 2, 3)

s = "Python"
print(s[1:5:2])    # "yh"
```
# 15.How can you reverse a string or list in python using slicing?
- The basic slicing syntax for any sequence is: sequence[start:stop:step]

- start: The index to start the slice (inclusive).

- stop: The index to end the slice (exclusive).

- step: The interval between elements. This can be positive or negative.


```python
s = "Python"
lst = [1, 2, 3, 4]
reversed_s = s[::-1]
reversed_lst = lst[::-1]
print(reversed_s)  # Output: "nohtyP"
print(reversed_lst)  # Output: [4, 3, 2, 1]
```

# 16. How would you optimize a recursive function to avoid maximum recursion depth errors in Python?
- Optimize by:

- Converting recursion to iteration.

- Using memoization to cache results.

- Tail recursion (though Python doesn't optimize it).

- Increase recursion limit (sys.setrecursionlimit()), but risky.

- Use generators for large traversals (e.g., tree/graph).

# 17.What is the difference between *args and **kwargs in function definitions, and how do you handle both in a single function?
- *args: Tuple of positional arguments.

- **kwargs: Dict of keyword arguments.

Handle both:
```python
def func(*args, **kwargs):
    for a in args: print(a)
    for k, v in kwargs.items(): print(f"{k} = {v}")
```

# 18.Explain how closures work in Python. Give a real-time example where closures are better than classes.
- A closure is a function that remembers variables from its enclosing scope.
- Real-world example (rate limiter):
```python
def rate_limiter(limit):
    calls = 0
    def limiter():
        nonlocal calls
        if calls < limit:
            calls += 1
            return True
        return False
    return limiter
```

# 19. When would you use a lambda function over a regular function in a production codebase?
- Use lambda for:

- Short, single-use functions.

- Passing as arguments (sorted(..., key=lambda x: x.id)).

- Avoid in:

- Complex logic.

- Debugging-intensive scenarios (unnamed = harder to trace).

# 20. How would you handle a situation where a loop inside a function is causing performance issues due to large data processing?
- Generators instead of lists.

- Built-in functions (map, sum, any).

- Batch processing.

- Multithreading or multiprocessing.

- Profiling tools to locate slow parts (cProfile, line_profiler).

# 21.What are generator functions and how do they help with memory optimization during iteration in Python?
- Yield values one at a time, don't store all results in memory.

Example:
```python
def gen():
    for i in range(1_000_000): yield i
```

# 22.Describe a situation where a higher-order function simplifies your code significantly in a real application.
- Example: Retry mechanism
```python
def retry(fn):
    def wrapper(*args, **kwargs):
        for _ in range(3):
            try: return fn(*args, **kwargs)
            except Exception: continue
    return wrapper
```

# 23. How do decorators work in Python, and how can you use them to enforce logging or authentication in a function?
-They wrap functions to add functionality.

Example: Authentication
```python
def authenticate(fn):
    def wrapper(user, *args):
        if not user.is_authenticated:
            raise PermissionError("Unauthorized")
        return fn(user, *args)
    return wrapper
```

# 24. How would you refactor deeply nested loops using functions to improve code readability and maintainability?
- Extract inner loops into separate named functions.

- Consider generators or list comprehensions.

- If I/O or async: break into coroutines.

# 25.What is tail recursion? Why is it not optimized by Python, and how can you convert a recursive function into an iterative one?
- Tail recursion places the recursive call as the final action.
- Python doesn't optimize tail recursion due to stack trace preservation.
- Convert to iteration:
```python
def factorial(n):
    result = 1
    while n > 1:
        result *= n
        n -= 1
    return result
```
# 26.How would you implement a retry mechanism for a function that might fail intermittently (e.g., API calls)?
```python
import time

def retry(fn, retries=3, delay=2):
    for i in range(retries):
        try:
            return fn()
        except Exception as e:
            time.sleep(delay)
    raise Exception("All retries failed.")
```

# 27.What are the implications of using mutable default arguments in function definitions, and how do you prevent related bugs?
- Avoid:
 ```python
def bad(x=[]):  # Shared between calls!
```
- Instead:
```python
def good(x=None):
    if x is None:
        x = []
```

# 28.How do you design a function that accepts another function and applies it to a dynamically sized dataset with custom loop logic?
```python
def apply_to_dataset(data, func):
    return [func(item) for item in data]
```
- For complex loops:
```python
def process(data, func):
    for chunk in custom_batch(data):
        yield func(chunk)
```

# 29.What is the difference between a function returning a generator and a function returning a list? When would you use each?
- Generator: memory-efficient, lazy.
- List: materialized immediately.
- Use generators for:
- Streaming large data (log files, APIs).

# 30.In a large data processing script, how would you design a loop that can be paused, resumed, or even run in parallel safely?
- Use:
- Generators + checkpoints.
- Joblib or multiprocessing for parallel.
- Pickle progress to disk for resume.

# 31.How do you implement caching or memoization inside a function without using external libraries like functools?
```python
def memoize(fn):
    cache = {}
    def wrapper(x):
        if x not in cache:
            cache[x] = fn(x)
        return cache[x]
    return wrapper
```

# 32.What is the difference between map, filter, and reduce in terms of loop behavior, and when should you avoid using them?
- map: transforms.
- filter: filters.
- reduce: accumulates.
- Avoid if:
- Logic is complex → prefer for loop.
- For clarity in large codebases.

# 33. How would you detect and safely handle infinite loops caused by logic errors in a production function?
- Set iteration counters or timeouts.
- Use break conditions carefully.
- In production: monitor execution time and raise alerts.

# 34.Explain the impact of using list comprehensions vs. traditional for-loops in terms of performance and readability.
- Faster and cleaner for simple expressions:
```python
squares = [x*x for x in range(10)]
```
- Avoid for multi-line logic or nested branches.

# 35. How can you design a function with nested loops to handle dynamic matrix-like input (e.g., processing CSV files with inconsistent rows)?
```python
def process_csv(matrix):
    for row in matrix:
        for i, value in enumerate(row):
            process_value(i, value)
```
- Use zip_longest for irregular rows (itertools).





  

  











































