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

## Core Python: Organizing Larger Programs

## Core Python: Classes and Object-orientation

## Unit Testing with Python

## Managing Python Packages and Virtual Environments

## Best Practices for Code Quality
