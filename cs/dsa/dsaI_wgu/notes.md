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

- Some scenarios for recursion:
  - GCD
  - factorial
  - fibonacci
  - Finding all possible combinations of a word's letters
  - Finding all possible subsets of a set of items
  - Finding all possible paths (traveling salesman)

- Binary search recursive algos
![image](https://user-images.githubusercontent.com/14286113/155868311-bd93f7de-eca5-425c-b52b-b6036bb4ab72.png)

- Constant time operation
  - operation that for a giving processor, always operates in the same amount of time regardless of input values
  - ![image](https://user-images.githubusercontent.com/14286113/155863249-b3c658cb-fd23-4f66-adf0-cc57b8865155.png)
  - ![image](https://user-images.githubusercontent.com/14286113/155863268-c638e04d-be0b-45bc-90c8-293d7db404d9.png)

- Runtime complexity 
  - `T(n)`, represents the number of constant time operations performed by the algorithn given an input size `n`
  - best case
    - the scenario that allows for minimum possible number of operations (can't be 0 operations)
    - Lower bound: `f(N) <= `T(N)`
  - worst case
    - the scenario that requires maximum possible number of operations
    - Upper bound: `f(N) >= `T(N)`
  - ![image](https://user-images.githubusercontent.com/14286113/155863944-396f5700-7fda-4464-8b4b-8baff9750477.png)

- Asymptotic notation
  - classification of runtime complexity that uses functions that indicate only the growth rate of a bounding function (ie uses only the leading term of a function)
  - _TODO: need to look this up more_
  - ![image](https://user-images.githubusercontent.com/14286113/155863985-6e822b6f-a3c4-4016-8f2c-f89b95a31c93.png)

- Space complexity
  - `S(N) = N + k`, represents the number of fixed-size memory units used by algorithm for an input size of `N` and auxilary space `K` which is a constant
  - input data + additional memory that doesnt include input data (for things like loop counter or object pointers)

- Big O notation
  - mathematical way of describing how a running time of an algorithm behaves in relation to the input size
  - uses growth rate instead of the exact function of running time to denote Big O notation for a running time
    - where `f(N)` is running time, if `f(N)` is sum of several terms, the highest order term (ie the fastest growth rate) is kept and others discarded
    - if `f(N)` has a term that is a product of several factors, all constants (that are not in terms of `N`) are omitted
    - ![image](https://user-images.githubusercontent.com/14286113/155865550-205ca612-0219-4aaf-8f90-2fb083b9cb12.png)

- Growth rates for different input sizes and different Big O complexities
![image](https://user-images.githubusercontent.com/14286113/155865587-88f40ee1-6b39-40b0-98cf-8210bc8cda6f.png)

- Runtime analysis
![image](https://user-images.githubusercontent.com/14286113/155865910-17b794f6-45b6-4bac-8056-7a1ccad11e56.png)

- Any nummber of constant number of constant time operations is `O(1)`
![image](https://user-images.githubusercontent.com/14286113/155866150-3b93dc3e-7d23-4c77-ae43-d85c56deebdf.png)

- Run time analysis of nested loops
![image](https://user-images.githubusercontent.com/14286113/155867979-d6b95112-81eb-4c87-b7f5-5a5f01af4c34.png)

- algorithm
  -  sequence of steps for accomplishing a task

- linear search
  - search algo that starts from the beginning of a list and checks each element until the search key is found or the end of the list is reached

```python
def linear_search(arr, key):
     for num, item in enumerate(arr):
             if item == key:
                     return num
     return -1
```

- binary search
  - search algorithm that requires list elements to be sorted and directly accessible for mutation 

  
