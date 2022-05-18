# Data Structures and Algorithms: Deep Dive Using C++

_[Link to course](https://www.udemy.com/course/data-structures-and-algorithms-deep-dive-using-c/)_

## 1: Intro

### 1-3: Data Structures and Memory usage

- Two parts of memory
  - External/ Secondary
  - Main

- Three parts of Main memory
  - Code Segment
    - Text
    - Data
    - BSS (blocks started by symbol)
  - Heap
  - Stack
  - Kernal space (omitted in the course)

- Three parts of Code segment
  - Text
    - code segment from memory
    - this is where code files are loaded into
    - code here access data in the data portion of Code Segment
  - Data
    - initialized data
    - contains the global and static variables initialized by the programmer
  - BSS
    - uninitialized data
    - contains global and static variables that have no value or are intialized to defaults

- Main memory memory addressing 
  - low memory addressing (0) starts at code segment portion
  - high memroy addressing (main memory max) ends at stack portion

- Memory addressing patterns
  - in stack portion, memory is filled up from top to bottom
  - in heap portion, memory is filled up from bottom to top

- Stack
  - LIFO 
  - stores information related to function invocation
  - stores variables in function scope
  - static memory allocation 
    - allocated during compile time (before program execution)
    - allocated for declared variables
    - less efficient
    - memory size cannot be changed once allocated
  - Ex of use: arrays

- Heap
  -  begins at the end of the CSS segment
  -  managed by malloc, realloc, and free
    -  memory can be freed
  -  dynamic memory allocation
    -  allocated during run time (during program execution)
    -  more efficient 
    - memory size can be changed
  - Ex of use: linked list

- Pointer is a variable that stores address of another variable

- Memory allocation
  - pointer variables that are declared are found in stack
  - when pointer variables are initialized using `new`, its stored in heap
  - the first memory address space of pointer variable in heap is the reference to the location in the stack
  - programmer needs to manually deallocate or release memory thats in the heap

### 1-4 Types of Data Structures

-  Physical data structures:
  - Arrays (static memory, contiguous blocks)
  - Linked List (dynamic memory, non-contiguous blocks)

- Logical Data structures (implemented by physical ds)
  - Stacks
  - Queues
  - Trees
  - Graphs

- Nonlinear data structures (sequential order)
  - Trees
  - Graphs

- Linear data structures (non sequential order)
  - arrays
  - linked lists
  - stacks 
  - queues

### 1-5 Linear List and Abstract Data Type

- Linear list
  - collection of ordered set of elements
  
- Linear List Operations
  - traversing - accessing data elements
  - inserting - adding data elements
  - deleting - removing data elements
  -
  
- Abstract Data Type
  - consists of the data instances and operations
  - operations are specified but its implemention is not described

## 2 - Essentials of C++ programming

### 2-7 Understanding Classes

**Access specifiers**
- private
  - default option
  - not accessibile outside of the class
- public
  - accessible from anywhere
- protected
  - accessible only among class inheritance chain

### 2-8 Classes and Member functions

**Member function types**
- constructors
- destructors
  - releases memory
  - executes some code before an object of the class is destroyed
- facilitators
  - utility operations
- accessors
  - used to retrieve data
- mutators
  - used to modify data

**Scope resolution operator**
- `::`
- used to implement member functions outside the class (interface?)
- so if you are defining a class that implements an interface, then you use `::` to refer to the member functions of the interface when implementing that function

### 2-11 Constructors and types of constructors

**Constructor characteristics**
- name of constructor is the same as the class name it belongs to
- there is no return type
- called automatically

**Basic Constructor syntax**
- ` className:: className()`

**Constructor Types**
- Default constructor
  - provided for us by default
  - _example skipped_
- Parameterized constructor
- Copy constructor
  - provided for us by default
  - copies contents of existing object into a new object
  - Syntax: `classname:: classname(classname & objectToBeCopied) {...}`
    - the `&` denotes that the argument reference (not a copy) should be used in the constructor

### 2-13 Constructor initalization

- There are different ways to initialize an object (parenthesis, curly brackets, etc)
- using brackets for initalization makes it good for readiblity as you wont confuse it for function declaration like you would with paranthesis
- _examples and details skipped!_

### 2-14 Dynmaic Memory Allocation

- static memory allocation occurs during compilation time
- dynamic memory allocation is where memory is handled during run time

**Dynamic memory allocation operators**
- new
  - used to allocate memory
  - Ex: `int *a;` --> this allocates a variable `a` in the stack memory area
    - `a = new int[10]` --> this creates an int array variable of size 10 in the heap memory area
    - the base address of `a` is held by `*a`
    - since arrays are contiguious, the subsequient memory address of `a` array elemnts are base adress + 4, 8, 12, etc
    - since memory was allocated like this, it must be deallocated by the programmer
- delete
  - used to deallocate (release) memory
  - ex: `delete []a;` --> this would destroy the array in the heap memory area and remove the pointer varaible in the stack memory area
    - the `[]` is only required for arrays...usually `delete a` is fine
