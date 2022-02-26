# C949: Data Structures & Algorithms I

## CH 3: ADTs and algorithms

### 3.1 Intro

- Algorithm
  - describes a sequence of steps to solve a computational problem or preform a calculation

- Computational problem
  - specifies an input, a question about the input that can be answered using a computer, and the desired output

- Efficient algorithm
  - one whose runtime increases no more than polynomially

- NP-complete problems
  - Set of problems for which no known efficient algorithm exists
  - Characteristics:
    - No efficient algos found to solve it
    - Not been proven that solution is impossible
    - if one NP-complete problem has efficiecnt algorithm, then all NP-complete problems can be solved efficiently
  - Purpose: if you know a problem is NP-complete, then you can focus on finding a good solution rather than the most optimal/efficient one

### 3.2 Data Structures

- data structure
  - a way of organizing, storing, and performing operations on data
  - operations: accessing/updating, searching, inserting, or removing data
 
- Basic Data structures
  - record
    - stores subitems (fields) with a name associated with each subitem
  - array
    - stores an ordered list of items, where each item is directly accessible by a positional index
  - linked list
    - stores an ordered list of items in nodes, where each node stores data and has a pointer to the next node
  - binary tree
    - where each node stores data and has up to 2 children: left and right childs
  - hash table
    - stores unorderd items by mapping (or hashing) each item to a location in an array
  - heap
    - max-heap
      - tree that minatains the simple property that a node's key is greater than or equal to the node's childrens' keys
    - min-heap
      - tree that maintains the simple property that a node's key is less than or equal to the node's childrens' keys
    - graph
      - where connections are respresented among items and ocnsists of vertices connected by edges
      - vertex - item in a graph
      - edge - connection between two vertices in a graph

### 3.3 Relation b/w DS and A

- DS defines structure & operations
- Algos implement operations and use DS for operations

### 3.4 Abstract Data Type

- Abstract data Type (ADT)
 - data type described by predefined user operations w/o its implementation
 - implementation is hidden 
 - can use different underlying DS for implementation
 - User only needs to know the interface of ADT

- Common ADTs
  - List
    - hold ordered data
    - DS: array, linked list
  - Stack
    - items are only inserted on or removed from top of a stack
    - DS: linked list
  - Queue
    - items are inserted at the end of the queue and removed from the front of the queue
    - DS: linked list
  - Dequeue
    - ADT in which items can be inserted and removed at both the front and back
    - DS: linked list
  - Bag
    - ADT for storing items in whcih the order does not matter and duplicate items are allowed
    - DS: array, linked list
  - Set
    - collection of distinct items
    - DS: BST, hash table
  - Priority Queue
    - where each item has a priortiy, and items with higher priority are closer to the front of the queue than items with lower priority
    - DS: Heap
  - Dictionary
    - ADT that associates or maps keys with values
    - DS: Hash table, BST

### 3.5 List ADT

- List
  - ADT for holding ordered data and having operations such as:
    - Append - insert at end of list
    - Prepend - insert at beg of list
    - InsertAfter
    - Remove - returns item or returns null if not found
    - Search
    - Print
    - PrintReverse
    - Sort - sorts in ascending order
    - IsEmpty
    - GetLength

### 3.6 Queue ADT

- Queue
  - ADT in which items are inserted at the end of the queue and removed from the front of the queueu
  - First-in First-out (FIFO)
  - Implemented with linked list, array, or vector
  - Operations:
    - Push
    - Pop
    - Peek
    - IsEmpty
    - GetLength

### 3.7 Applications of ADTs

- Supports abstraction by hiding implementation and providing a well-defined set of operations for using the ADT
- Enables programmers to focus on higher-level operations thus improving programmer efficiency

## Algorithms

*Notes from ch 9-11*
