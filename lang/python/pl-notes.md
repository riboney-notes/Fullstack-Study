# Core Python
_notes based on pluralsight python courses_

## Core Python: Getting Started
[link](https://app.pluralsight.com/library/courses/getting-started-python-core)

- Signficant whitespace rules
  - 4 spaces
  - Dont mix spaces and tabs
- refer to Zen of python for clean code principles
- can see documenation for particular python fucntion or class by doing `help(...)` in REPL
- Different syntax for importing
  - import package
  - from package import function
  - from package import function as func
  - from words import *
  - from words import (func_1, func_2)
- Division
  - `/` returns floating point value
  - `//` returns integer
- Exponentation is done with `**`
- Scalar types
  - int
  - float
  - None
  - bool
- Calculations with float and int results in a float
- None is like null
  - its never printed to console
- Bool
  - True False
  - bool() can produce boolean based on truthy and falsey values
    - `bool("")` is False
    - `bool([])` is False
- if/elif/else
- Create multiline strings with 3 quotes
- raw strings prefixed with `r` can be used to print strings as they are written 
- encode/ decode can be uses to convert data from and to string and bytes
- lists: []
- dictionaries: {}
- for loops
  - for each syntax:
  ```python
  for item in iterable:
    #...
  ```
- byte literals are prefixed with lowercase `b`

### Modularity

- defining functions
  - `def funcName(): ....`
- `__name__`
  - specially named variable allowing to detect whether a module is run as a script or imported into another module
  - Ex:
  ```python
  # if running as script, execute function
  if __name__ == '__main__':
    fetch_words()
  # else import as module and don't execute
  ```
- Good to have two blank lines between function definitions

### Objects and types
- id()
  - returns a unique integer id for an object that is constant for the life of the object
- python doesn't have variables that hold primitive values
  - python's variables are named references to objects
- value vs identity equality
  - if p = [4,5,6] and q = [4,5,6] then
    - p == q -> true and p is q -> false
- values passed into functions are not copied
  - modifying values inside functions will modify the original value
  - python functions are pass by reference
- function parameters can have default value like in javascript `def func(arg1, arg2='default')`
- You can multiply a string by a number to get that many duplicates of that string
- pyhton functions arguments don't adhere to position always
  - you can use the same parameter name to assign values to the appropriate parameter
- default arguments are evealuated only once when def is executed
- better to avoid using default arguments and use immutable values and assign default in the function body
- scopes
  - local: inside current function
  - enclosing: inside enclosing function
  - global: top level of the module
    - use `global` key word to refer to the variable in the global scope from within function
    - We use global keyword to read and write a global variable inside a function
  - built-in: special builtins module

### Collections

- tuples
  - example = ()
  - similiar to list except it is unchangeable
  - allows duplicate values
  - tuple destruction ex: `lower, upper = minmax(..)`
    - swapping elements with destructuing: a=1, b=2; a,b = b, a; a=2, b=1
- better to use str.join() instead of + to join strings (performance)
  - `';'.join([...])`
- range() allows you to generate consecutive numbers in the sepcified range
  - not good practice to use range() and len() in for loops; use enumerate() instead
- to get last number in list, use `-1` as the index
  - dont use length-1
- slicing (ex: s[1:-1]) lets you select elements within a range in an array
  - use `s[:]` to produce a copy

## Core Python: Organizing Larger Programs

## Core Python: Classes and Object-orientation

## Unit Testing with Python

## Managing Python Packages and Virtual Environments

- Best practices
  - always work inside a virtual environment when working with packages
    - lets you install packages for local projects
  - don't use pip with sudo

- `pip list`
  - lists all currently installed pyhton packages

- Virtual Environment
  - isolated context for installing packages
    - isolated so it won't interfere with other package installations/ configs

### Setting up project with virtual environments

- Create venv: `python3 -m venv venv`
  - Activate venv: `project\Scripts\activate.bat`
    - it works if you can see the environment name in parenthesis
  - get out of venv: `deactivate`

- Syncing dependencies with team
  - `python -m pip freeze > requirements.txt` will take local dependencies and populate a requirments text file with it
  - `python -m pip install -r requirements.txt`: installs dependencies listed by requirements.txt
    - activate venv first
- virtual enviroments should be separate from projects
  - so they should be gitignored
- you can separate dependencies by having different requirement files

## Best Practices for Code Quality
