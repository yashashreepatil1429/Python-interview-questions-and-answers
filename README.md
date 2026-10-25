Python-interview-questions-and-answers

20 Common Python Interview Questions and Answers

1. What are the main features of Python?

Python is a high-level, general-purpose language known for readable syntax, dynamic typing, and a large standard library. It supports procedural, object-oriented, and functional programming, and runs on multiple operating systems.

2. What is the difference between a list and a tuple?

A list is mutable, so its contents can be changed after creation. A tuple is immutable. Use a list for a collection that changes and a tuple for a fixed grouping of values.

```python
items = [1, 2, 3]
items[0] = 10

coordinates = (4, 5)
```

3. What is the difference between `==` and `is`?

`==` compares values for equality. `is` checks whether two references point to the same object. Use `is None` to test for `None`.

4. What are mutable and immutable types?

Mutable objects can change in place; examples include lists, dictionaries, and sets. Immutable objects cannot be changed after creation; examples include integers, strings, and tuples (though a tuple can contain mutable objects).

5. What are `*args` and `**kwargs`?

`*args` collects extra positional arguments into a tuple. `**kwargs` collects extra keyword arguments into a dictionary.

```python
def show(first, *args, **kwargs):
	print(first, args, kwargs)
```

6. What is a Python dictionary, and what can be used as a key?

A dictionary stores key-value pairs and provides efficient average-case lookup by key. Keys must be hashable, which generally means their equality and hash stay stable; strings, numbers, and many tuples of immutable values are common keys.

7. What is a list comprehension?

A list comprehension is a concise way to create a list from an iterable, optionally filtering its items.

```python
squares = [number * number for number in range(5)]
```

8. What is the difference between an iterable and an iterator?

An iterable can produce an iterator, usually through `iter()`. An iterator produces values one at a time with `next()` and keeps track of its position. Lists are iterable; generators are iterators.

9. What is a generator, and when would you use one?

A generator produces values lazily, one at a time, instead of building the whole result in memory. Define one with a function containing `yield`, especially for large or streamed sequences.

```python
def count_up_to(limit):
	for number in range(limit):
		yield number
```

10. What is the difference between `return` and `yield`?

`return` ends a function and provides its result. `yield` pauses a generator function and produces a value; the function can resume later from that point.

11. What is a decorator?

A decorator is a callable that wraps another function or class to add or modify behavior without changing the wrapped object's source. It is commonly applied with `@decorator` syntax.

12. What is a lambda function?

A lambda is a small anonymous function consisting of a single expression. It is useful for short callbacks, such as a sorting key, but regular `def` functions are clearer for more involved logic.

```python
names = ["Ada", "grace"]
names.sort(key=lambda name: name.lower())
```

13. Why should mutable default arguments be avoided?

Default argument values are evaluated once when the function is defined, not each time it is called. A mutable default can therefore retain changes between calls. Use `None` and create a new object inside the function instead.

```python
def add_item(item, items=None):
	if items is None:
		items = []
	items.append(item)
	return items
```

14. What is the difference between a shallow copy and a deep copy?

A shallow copy creates a new outer object but shares references to nested objects. A deep copy recursively copies nested objects too. The `copy` module provides `copy.copy()` and `copy.deepcopy()`.

15. How does exception handling work in Python?

Use `try` for code that may fail, `except` to handle specific exceptions, `else` for code that runs when no exception occurs, and `finally` for cleanup that should always run.

16. What is a context manager?

A context manager manages setup and cleanup around a block of code. The `with` statement uses one; for example, it closes a file even if an exception occurs.

```python
with open("notes.txt", encoding="utf-8") as file:
	contents = file.read()
```

17. What is the difference between a module and a package?

A module is a Python file that can define code for reuse. A package organizes related modules under a package namespace, typically using a directory (often with an `__init__.py` file; namespace packages can work without one).

18. What is a virtual environment, and why use one?

A virtual environment isolates a project's installed packages from other projects and the system Python. This helps avoid dependency conflicts and makes project setup more reproducible.

19. What is the Global Interpreter Lock (GIL)?

In CPython, the GIL allows only one thread at a time to execute Python bytecode within a process. Threads can still help with I/O-bound work, while CPU-bound parallel work often uses multiprocessing or other approaches. Other Python implementations may differ.

20. How does Python manage memory?

Python manages object memory automatically. CPython primarily uses reference counting and supplements it with a cyclic garbage collector to reclaim unreachable reference cycles. Application code generally should not manually free objects.