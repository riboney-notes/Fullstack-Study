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
