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



























