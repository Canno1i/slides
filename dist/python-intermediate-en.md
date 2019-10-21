# {{title}}

## Presentation and code

Presentations available at: https://karuga.eu/courses-presentations

Code available at: https://github.com/marko-knoebl/courses-code

## Your Trainer

Marko Knöbl

- Frontend Web-Development
  - JavaScript
  - React, Angular
- Programming
  - Python, JavaScript

## Introduction of Participants

- Name
- Company
- Current Projects
- Prior Knowledge
- Expectations

## Organizational

- Duration
- Breaks
- Materials
- Questions, Feedback?

# Data types in Python

## Basic data types

- int
- float
- bool
- NoneType
- string
- bytes

## Collections

- list
- tuple
- dict
- set

## Other data types

- complex
- frozenset
- bytearray
- OrderedDict
- NamedTuple

# None

## None

The expression `None` is for "nothing" - analogous to `null` or `undefined` in other languages.

It may be used if a certain value is unknown

```py
users = [
  ["John", "Doe", "1976-10-23"],
  ["Jane", "Doe", None]
]
```

## None

`None` is a Singleton:

- there is only ever a single instance of it inside a running Python program
- multiple variables may refer to that same instance

## Comparisons via "is"

The keyword `is` checks whether two references / names refer to the same object.

```py
a = [1, 2]
b = a
x = [1, 2]

a == b # True
a is b # True
a == x # True
a is x # False
```

## None and "is"

As `None` is a singleton we can check for it via `is None`:

```py
if a is None:
    print("a is None")
```

# bool

## bool

`True` or `False`

```py
a = True
if a:
    print('hello')
```

## bool

Internally `False` behaves almost like `0` and `True` behaves almost like `1`

```py
False + True # 1
```

# Numbers

## int

integers of arbitrary size

## int

Other numeral systems:

```py
a = 42
b = 0o52
c = 0x2a
d = 0b101010
```

```py
e = int('101010', 2)
```

## float

64 bit float

```py
a = 2.3
b = .2
c = 6e23
d = float('nan')
e = float('inf')
```

## float

Be cautious of rounding errors: Some numbers cannot be represented as floating point numbers, they will always be rounded

e.g.: `1/3`

A computer is also unable to represent numbers like `0.1` or `0.2` exactly

example: `0.3 - 0.2` evaluates to `0.09999999999999998`

In general a 64-bit float will be exact for about 15 decimal places.

## float

_IEEE 754_: standardized floating point arithmetic

Python mostly acts as defined in the standard

deviation from the standard: in some cases Python will throw exceptions where the standard produces a result - e.g. `1.0/0.0`

Special numbers in IEEE 754:

- `inf` and `-inf` (infinite values)
- `nan` (not-a-number: undefined / unknown value)

## complex

```py
a = 2 + 3j
```

## Augmented assignment

For binary operators there are so-called _augmented assignments_:

```py
a = a + 1
```

short form (augmented assignment):

```py
a += 1
```

## Operations with numbers

- Integer division: `10 // 3`
- Remainder: `10 % 3`
- Power: `2 ** 3`

# Character encodings

## Unicode characters

_Unicode_: catalog of over 100,000 international characters, each with a unique identifying name and number (usually written in hexadecimal)

examples:

- _K_: U+004B (_Latin capital letter K_)
- _?_: U+003F (_Question mark_)
- _ä_: U+00E4 (_Latin small letter a with a diaeresis_)
- _€_: U+20AC (_Euro sign_)
- 🙂: U+1F642 (_Slightly smiling face_)

[tables of all Unicode characters](https://en.wikibooks.org/wiki/Unicode/Character_reference)

## Character encodings

_Character encoding_ = mapping of characters to bit sequences

- _ASCII_: encodes the first 128 Unicode characters, can represent characters like _A_, _!_, _\$_, _space_, _line break_
- _Latin1_: encodes the first 256 Unicode characters, can represent ASCII characters and characters like _ä_, _á_, _ß_, _§_
- _UTF-8_, _UTF-16_, _UTF-32_: encode all Unicode characters

A character encoding is necessary in order to write text to disk or transfer it over the network

## Character encodings

Examples in ASCII / Latin1 / UTF-8:

- `!` ↔ `00100001`
- `A` ↔ `01000001`
- `a` ↔ `01100001`

Examples in Latin1:

- `Ä` ↔ `11000100`

Examples in UTF-8:

- `Ä` ↔ `11000011 10100100`
- `🙂` ↔ `11110000 10011111 10011001 10000010`

## UTF-8

In many areas (in particular on the web) _UTF-8_ has become the standard text encoding

In UTF-8 the first 128 Unicode characters can be encoded in just 8 bit

All other characters need either 16, 24 or 32 bit

## UTF-32

UTF-32 encodes the Unicode code points directly

Depending on the area of application the byte order may differ (big endian or little endian)

example:

🙂 (U+1F642) ↔ `00 01 F6 42` (big endian) or `42 F6 01 00` (little endian)

## Line breaks

Line breaks can be represented by the characters `LF` (line feed, `U+000A`) and / or `CR` (carriage return, `U+000D`)

- `LF`: Standard on Linux, MacOS
- `CRLF`: Standard on Windows, in network protocols like HTTP

In string literals `LF` is often represented by `\n` and `CR` is represented by `\r`

# Strings

## Strings

In Python 3 strings are sequences of Unicode characters

## String literals

Examples:

```py
a = "test"
b = 'test'
```

## Multi-line string literals

```py
a = """this
is a multi-line
string literal.
"""
```

## Escape sequences

Some characters may be entered via so-called _escape sequences_:

```py
a = "He said:\n\"Hi!\""
```

## Escape sequences

- `\'` → `'`
- `\"` → `"`
- `\\` → `\`
- `\n` → Line Feed (line separator on Unix)
- `\r\n` → Carriage Return + Line Feed (line separator on Windows)
- `\t` → Tab
- `\xHH` or `\uHHHH` or `\UHHHHHHHH` → Unicode-Codepoint (hexadecimal)

## Raw Strings

If we don't need to use any escape sequences in a string:

```py
path = r"C:\documents\foo\news.txt"
```

This can be useful when writing Windows paths and regular expressions

## String methods

- `.lower()`
- `.upper()`

## String methods

- `.startswith(...)`
- `.endswith(".txt")`

## String methods

- `.center(10)`
- `.ljust(10)`
- `.rjust(10)`

## String methods

- `.strip()`
- `.split(' ')`
- `.splitlines()`
- `.join()`

## Exercise: formatting Othello

Source:

http://www.gutenberg.org/cache/epub/2267/pg2267.txt

tasks:

- remove leading whitespace of each line
- add a line number to the end of each line and place the line number right-aligned at character 70
- (place line numbers only in every 5th line)
- (instead of placing line numbers at character 70, use the longest line as a reference)

# String formatting

## String formatting

String formatting = placing values in strings

Methods:

```py
greeting = "Hello, " + name + "!"
```

```py
greeting = f"Hello, {name}!"
```

## String formatting: methods

```py
city = 'Vienna'
temperature = 23.7

# rather obsolete
'weather in %s: %f°C' % (city, temperature)

'weather in {0}: {1}°C'.format(city, temperature)
'weather in {}: {}°C'.format(city, temperature)
'weather in {c}: {t}°C'.format(c=city, t=temperature)

f'weather in {city}: {temperature}°C'
```

## Format specification

```py
t = 333.333
f'{t:.4f}°K' # 333.3330°K
f'{t:.4g}°K' # 333.3°K
```

https://mkaz.blog/code/python-string-format-cookbook/

# Lists

## Lists

Lists are mutable sequences of objects; they are usually used to store homogenous entries of the same type and structure

```py
primes = [2, 3, 5, 7, 11]

users = ["Alice", "Bob", "Charlie"]
```

## Operations on lists

The following operations will also work on other _sequences_ - e.g. tuples, strings or bytes

- accessing elements (via index): `users[2]`
- accessing multiple elements (sublist): `users[2:4]`
- concatenation: `users + users`
- repetition: `3 * users`
- length: `len(users)`
- for loop: `for user in users:`
- if clause : `if 'Tim' in users:`

## Operations on lists - mutations

Lists are the only sequences that can be mutated:

- appending: `users.append("Dan")`
- removing the last element: `users.pop()`
- removing an element by index: `users.pop(2)`

## Sorting lists

```py
l.sort()
```

```py
l.sort(key=...)
```

## Exercises

- shuffling cards
- list of prime numbers

# Tuples

## Tuples

```py
date = (1973, 10, 23)
```

- area of application: similar to dicts
- behavior: similar to lists

## Tuples

Area of application: similar to dicts:

```py
point_dict = {"x": 2, "y": 4}
point_tuple = (2, 4)

date_dict = {
  "year": 1973,
  "month": 10,
  "day": 23
}
date_tuple = (1973, 10, 23)
```

Each entry in a tuple has a specific meaning

## Tuples

Behavior: similar to lists:

```py
date_tuple[0] # 1973
len(date_tuple) # 3
```

Unlike lists, tuples are immutable (no `.append` / `.pop` / ...)

## Creating tuples

Entries are separated by commas, usually surrounded by round brackets.

```py
empty_tuple = ()
single_value = ('Thomas', )
two_values = ('Thomas', 'Smith')
two_values = 'Thomas', 'Smith'
```

## Unpacking (of tuples)

```py
time = (23, 45, 0)

hour, minute, second = time
```

swapping variables:

```py
a, b = b, a
```

# Bytes

## Bytes

= Sequence of numbers in the range of 0 to 255

```py
m = bytes([0, 0x40, 0x70, 0xa0])
```

```
m[1] == 64
m[2] == 160
```

## Bytes

Standard representation in Python:

```py
print(bytes([0x00, 0x40, 0x70, 0xa0]))
```

```py
b'\x00@p\xa0'
```

Where possible, bytes will be represented by ASCII characters; otherwise their hex code will be shown

The `b` signifies a byte string literal

## Bytes and Strings

Bytes can hold arbitrary data, but often they will hold encoded text

If we know the encoding we can convert between bytes and strings:

```py
'ä'.encode('utf-8')
# b'\xc3\xa4'
```

```py
b'\xc3\xa4'.decode('utf-8')
# 'ä'
```

## Bytes and Strings

Storage media and networks will only handle bytes; in order to read a text file from disk or from the network we need to know / specify the encoding

# Sequences

## Sequences

Python Sequences consist of other Python objects

examples:

- lists
- tuples
- strings
- bytes

## Operations on sequences

- accessing elements (via index): `s[2]`
- accessing multiple elements: `s[2:4]`
- concatenation: `s + t`
- repetition: `3 * s`
- length: `len(s)`
- for loop: `for el in s:`
- if clause : `if el in s:`

## Operations

Accessing elements

```py
users = ['mike', 'tim', 'theresa']

users[0] # 'mike'
users[-1] # 'theresa'
```

## Operations

Changing elements

(if the sequence is mutable)

```py
users = ['mike', 'tim', 'theresa']

users[0] = 'molly'
```

## Operations

Accessing multiple elements

```py
users = ['mike', 'tim', 'theresa']

users[0:2] # ['mike', 'tim']
```

## Operations

Concatenation

```py
users = ['mike', 'tim', 'theresa']

new_users = users + ['tina', 'michelle']
```

## Operations

Repetition

```py
users = ['mike', 'tim', 'theresa']

new_users = users * 3
```

## Operations

Length

```py
users = ['mike', 'tim', 'theresa']

print(len(users))
```

## Operations

for loop

```py
users = ['mike', 'tim', 'theresa']

for user in users:
    print(user.upper())
```

# Dictionaries

## Dictionaries

Dictionaries are mappings of keys to values

```py
person = {
    "first_name": "John",
    "last_name": "Doe",
    "nationality": "Canada",
    "birth_year": 1980
}
```

## Dictionaries

Accessing entries

```py
person["first_name"] # "John"
```

## Dictionaries

Iterating over dictionaries

```py
for entry in person:
    print(entry)
```

This will yield the keys: `"first_name"`, `"last_name"`, `"nationality"`, `"birth_year"`

Since Python 3.7 the keys will always remain in insertion order

## Dictionaries

Iterating over key-value-pairs:

```py
for key, value in person.items():
    print(f'{key}, {value}')
```

see also: tuples

## Operations on dictionaries

```py
d = {0: 'zero', 1: 'one', 2: 'two'}

d[2]
d[2] = 'TWO'
d[3] # KeyError
d.get(3) # None

d.keys()
d.items()

d1.update(d2)
```

## Valid keys

Any immutable object can act as a dictionary key. The most common types of keys are strings.

## Exercises

- vocabulary trainer
  - read a (JSON) file
  - create a data model with dictionaries
  - randomly pick an entry
- todo list

# Comprehensions

## List comprehensions

_List comprehensions_ enable the creation of lists based on existing lists

In other programming languages this is often done via `map` and `filter`

## List comprehensions

_Transforming each entry_:

```py
names = ["Alice", "Bob", "Charlie"]

uppercase_names = [name.upper() for name in names]
```

result:

```py
["ALICE", "BOB", "CHARLIE"]
```

## List comprehensions

_Filtering_:

```py
amounts = [10, -7, 8, 19, -2]

positive_amounts = [amount for amount in amounts if amount > 0]
```

result:

```py
[10, 8, 19]
```

## List comprehensions

Generic syntax:

```py
new_list = [new_entry for entry in old_list]

new_list = [new_entry for entry in old_list if condition]
```

## Dictionary comprehensions

```py
colors: {
  'red': '#ff0000',
  'blue': '#0000ff',
  'green': '#008000'
}

m_colors = { color: colors[color][1:] for color in colors}
```

## Exercises

- todo list: add functionality to remove completed entries

# Object-oriented programming and classes

## Object orientation in Python: "Everything is an object"

```py
a = 20

a.to_bytes(1, "big")

"hello".upper()
```

## Types and instances

```py
message = "hello"

type(message)

isinstance(message, str)
```

## Classes

Classes may represent _various_ things, e.g.:

- a Message inside an e-mail program
- a user of a website
- a car in a racing game
- a shopping basket in an online shop
- a bank account
- ...

## Classes

The definition of a class usually encompasses:

- a "data structure" (attributes)
- a "behavior" (methods)

## Classes

example: class `BankAccount`

- "data structure" (attributes)
- "behavior" (methods)

## Defining classes

```py
class MyClass():

    # the method __init__ initializes the object
    def __init__(self):
        # inside any method, self will refer
        # to the current instance of the class
        self.message = "hello"

instance = MyClass()
instance.message # "hello"
```

## Inheritance

```py
class Person():
    ...

class Admin(Person):
    ...
```

## Example: class "Length"

```py
a = Length(2.54, "cm")
b = Length(3, "in")

a.unit
a.value
```

## Exercise: classes "TodoList" and "Todo"

```py
tdl = TodoList("groceries")

tdl.add("milk")
tdl.add("bread")

print(tdl.todos)
tdl.todos[0].toggle()

tdl.stats() # {open: 1, completed: 1}
```

# Control structures

## Control structures

- `if`
- loops
  - `while`
  - `for ... in ...`
  - `for ... in range()`
- `try ... except ...`

# if

## if

From a previous example:

```py
if age_seconds < 1000000000:
    print("You are less than 1 billion seconds old")
else:
    print("You are older than 1 billion seconds")
```

## Conditions

When using conditions for `if` / `while` we usually use expressions that evaluate to boolean values.

However, we can also use other types:

```py
a = 0
if a: ...

name = input("enter your name")
if name: ...

products = []
if products: ...
```

These types are converted to boolean values before being used as criteria for the if condition.

## Conditions

Any value may be used as a condition in Python. Most values will be "truthy".

Only these values are considered "falsy" - calling `bool(...)` will return `False`:

- `False`
- `0`, `0.0`
- `None`
- empty collections / sequences (`""`, `[]`, `()`, `{}`)
- (before Python 3.5: `datetime.time(0, 0, 0)`)

## Conditions

Not "pythonic":

```py
name = input("Enter your name:")
if name != "":
    ...
```

"pythonic" version:

```py
name = input("Enter your name:")
if name:
    ...
```

## if expressions

An expression that evaluates to one of two possibilities based on a boolean criterion

```py
size = 'small' if length < 110 else 'big'
```

in other languages this could be written as:

```js
// JavaScript
size = length < 110 ? 'small' : 'big';
```

# For loops

## Itertools

Itertools: Module for creating iterable elements

Example:

```py
for i in count():
    print(i)
    if i >= 5:
        break

# 0 1 2 3 4 5
```

## For loops with tuple unpacking

Recap: tuple unpacking

```py
time = (23, 45, 0)

hour, minute, second = time
```

## For loops with tuple unpacking

Enumerating list items:

```py
l = ['Alice', 'Bob', 'Charlie']

for i, name in enumerate(l):
    print(f'{i}: {name}')
```

Enumerate returns a data structure that behaves like this list:

```py
[(0, 'Alice'), (1, 'Bob'), (2, 'Charlie')]
```

## For loops with tuple unpacking

Listing directory contents (including subfolders) via `os.walk`:

```py
import os

for directory, dirs, files in os.walk("C:\\"):
    print(f"{directory} {files}")
```

```
C:\ []
C:\PerfLogs []
C:\Program Files []
C:\ProgramData []
...
```

# Exceptions

## Types of exceptions

- AttributeError, IndexError, KeyError
- NameError
- TypeError
- ValueError
- IOError
- ZeroDivisionError
- ...

Exercise: try and trigger all of the above exceptions

## Catching exceptions

```py
age_str = input("Enter your age")
try:
    age = int(age_str)
except ValueError:
    print("Could not parse input as number")
```

## Catching exceptions

```py
age_str = input("Enter your age")
try:
    age = int(age_str)
except ValueError as e:
    print("Could not parse input as number")
    print(e)
    print(e.args)
```

## Catching exceptions

Catching multiple types of exceptions:

```py
try:
    file = open("log.txt", encoding="utf-8")
except FileNotFoundError:
    print("could not find log file")
except PermissionError:
    print("reading of file is not permitted")
except Exception:
    print("error when reading file")
```

## Catching exceptions

Using `finally`:

```py
try:
    file = open("log.txt", "w", encoding="utf-8")
    file.write("abc")
    file.write("def")
except IOError:
    print("Error when writing to file")
finally:
    file.close()
```

## Catching exceptions

Using `else`:

```py
try:
    file = open("log.txt", "w", encoding="utf-8")
except IOError:
    print("could not open file")
else:
    # no errors expected here
    file.write("abc")
    file.write("def")
file.close()
```

## Re-raising exceptions

```py
try:
    ...
except ClientError as e
    if "DryRunOperation" not in str(e):
        raise
```

## Python philosophy: EAFP

LBYL: _Look before you leap_

EAFP: _It's easier to ask for forgiveness than permission_

(example: parsing numbers)

# Raising exceptions

## Raising exceptions

```py
raise ValueError('test')
```

## Re-raising caught exceptions

```py
try:
    ...
except ClientError as e
    if "DryRunOperation" not in str(e):
        raise
```

## Custom exceptions

We can define custom exceptions as subclasses of other exception classes:

```py
class MoneyParseException(Exception):
    pass

raise MoneyParseException()
```

# Modules and packages

## Modules and packages

- Module = collection of Python objects that can be imported
- Package = collection of modules

(packages are actually a special type of modules)

## Example imports

- `urllib` = package
- `urllib.request` = module
- `urllib.request.urlopen` = function

<!-- list separator -->

- `sys` = module
- `sys.path` = object

## Example imports

Typical imports:

```py
import module1
import module2
from package3 import module3a, module3b
from module4 import object4a, object4b
from package5.module5 import object5a, object5b
```

Specific examples:

```py
import os
import sys
from urllib import request, response
from math import sqrt, pi
from http.client import HTTPConnection, HTTPSConnection
```

## Shorter names for imports

Typically used in an interactive console to save keystrokes:

Short names:

```py
import numpy as np
import matplotlib.pyplot as plt
import tkinter as tk
```

Importing everything from a module (usually not recommended):

```py
from math import *
```

## Automatic import of submodules

When importing _some_ packages, submodules will be imported automatically.

Examples:

```py
import os
import numpy as np

os.path.join(...)
np.random.randint(10)
```

Counterexample - this will fail:

```py
import urllib

urllib.request.urlopen(...)
```

## Conventions for imports

- all imports in a Python file _should_ be at the start of the file
- imports _should_ be split into three groups:
  - imports from the standard library
  - imports from other libraries
  - imports within the project

# Custom modules

## Custom modules

Goal: creating a custom module that can be used like this:

```py
from foo import a, b
```

## Custom modules

Simple module as a Python file:

```py
# foo.py
a = 1
b = 2
```

## Custom modules

Module as a directory:

```
- foo/
  - __init__.py
```

```py
# __init__.py
a = 1
b = 2
```

## Custom modules

Module as a directory with separated defintions:

```
- foo/
  - __init__.py
  - _a_mod.py
  - _b_mod.py
```

```py
# __init__.py
from _a_mod import a
from _b_mod import b
```

## Custom packages

Goal: creating a custom package that can be used like this:

```py
from foo import bar

print(bar.a)
print(bar.b)
```

## Custom packages

```
- foo/
  - bar.py
```

## Resolving imports

Search order:

- directory of the Python script that was executed
- standard library
- external libraries

Avoid name clashes with existing modules / packages!

## Resolving imports

To see all search paths for imports:

```py
import sys
print(sys.path)
```

## Compilation of modules

Imported modules will be saved in a compiled form, making subsequent loading of the modules faster.

Compiled versions will be saved in the folder `__pycache__`

# PIP & pipenv

## PIP

_PIP_ = Package manager for Python

Simple usage:

```bash
pip install requests numpy
```

Packages and their dependencies are looked up in the Python Package Index: https://pypi.org/

## PIP

Installing specific Versions:

```
pip install requests==1.1
pip install numpy>=1.16
```

## PIP

dependency list ina requirements file that can be shared with others:

requirements.txt:

```
requests==1.1
numpy>=1.16
```

```bash
pip install -r requirements.txt
```

## Pipenv

_Pipenv_: virtual environments that enable installation of different package versions per project

## Pipenv

```bash
pip install pipenv
```

## Pipenv

Using pipenv:

```bash
pipenv install requests
pipenv install numpy
```

This creates two files:

- _Pipfile_: general dependency information
- _Pipfile.lock_: exact version numbers

## Pipenv

Executing Python scripts in a PIP environment:

```bash
pipenv run python foo.py
```

# Functions

## Arbitrary number of Arguments (args / kwargs)

```py
def foo(*args, **kwargs):
    print(args)
    print(kwargs)

foo("one", "two", x="hello")
# args: ("one", "two")
# kwargs: {"x": "hello"}
```

`args` will be a tuple, `kwargs` will be a dictionary

## Arbitrary number of Arguments (args / kwargs)

Task: recreate `range()` by using a while loop

## Unpacking of parameter lists

```py
numbers = ["one", "two", "three"]

# equivalent:
print(numbers[0], numbers[1], numbers[2])

print(*numbers)
```

## Global and local scope

`global` / `nonlocal`

change the behavior of _assignments_

## Call by sharing

In Python values are passed to functions via _call by sharing_ (similar to _call by reference_ in other languages)

This means: A function _may_ mutate parameters that are passed in - and we should usually make sure not to do so

## Call by sharing

Example:

```py
def modify_a(mylist):
    mylist.append(1)
    return mylist

def modify_b(mylist):
    return mylist + [1]

list_a = [1, 2]
list_a_mod = modify_a(list_a)
list_b = [1, 2]
list_b_mod = modify_b(list_b)
```

(results on next slide)

## Call by sharing

```py
list_a_mod # [1, 2, 1]
list_b_mod # [1, 2, 1]
list_a # [1, 2, 1]
list_b # [1, 2]
```

# Pure functions

## Pure functions

Pure functions are functions which only interact with their environment via input parameters and return values

in particular, this means:

- no reading / writing of variables outside of the function
- no I/O (no access to disk / network)
- no mutating of objects that are passed in

## Pure functions

Advantages of pure functions

- easily reusable (as they are independent of their environment)
- easy to test

## Pure functions

Example of a function which isn't pure:

```py
def remove_negatives(numbers):
    i = 0
    while i < len(numbers):
        if numbers[i] < 0:
            numbers.pop(i)
    return numbers

a = [2, 4, -1, -2, 0]
b = remove_negatives(a)
```

## Pure functions

A pure function as an alternative:

```py
def remove_negatives(numbers):
    nonnegatives = []
    for n in numbers:
        if n >= 0:
            nonnegatives.append(n)
    return nonnegatives
```

Note: in Python the ideal solution would be using list comprehensions

# Recursive functions

## Recursive functions

Functions that call themselves

## Recursive function

Task: fibonacci sequence

```py
# 0 1 1 2 3 5 8 13 21 34 55 89 ...

fib(3)

fib(25)
```

## Recursion with Turtle graphics

## Exercises

- babylonian method for finding square roots
- trees with turtle graphics

# Python versions

## Python versions

Python 2 vs Python 3

## Strings and Bytes

major change in Python 3:

strict separation of text (strings) and binary data (bytes)

in Python 2: data types `bytes`, `str` and `unicode`

## Print

Python 2:

```py
print "a",
```

Python 3:

```py
print("a", end="")
```

## Division

Python 2:

```py
10 / 3    # 3
```

## range

in Python 2: `range()` returns a list, `xrange()` returns an object that saves on memory

in Python 3: `range()` returns an object that saves on memory

## input

in Python 2: `input()` will evaluate / execute the input, `raw_input()` returns a string

in Python 3: `input()` returns a string

## \_\_future\_\_ imports

Getting some of the behavior of Python 3 in Python 2:

```py
from __future__ import print_function
from __future__ import unicode_literals
from __future__ import division
```

## Python-Future

Compatibility layer between Python 2 and Python 3

Enables supporting both Python 2 and Python 3 from the same codebase

