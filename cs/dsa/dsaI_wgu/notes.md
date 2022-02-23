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
