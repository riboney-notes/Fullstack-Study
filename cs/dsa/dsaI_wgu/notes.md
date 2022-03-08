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
     for i in range(len(arr)):
             if arr[i] == key:
                     return i
     return -1
```

- binary search
  - search algorithm that requires list elements to be sorted and directly accessible for mutation before it can search for key in list by this algorithm:
    - Find middle element of list and check if it matches key; if it does, then return index of this element
    - if not, then see if middle element is lower or higher than key and continue the search process with the correct sub list
  - max number of steps: log(2)N + 1
  ```python
  def binary_search(arr, lowerIndex, higherIndex, key):
    if higherIndex >= lowerIndex:
      mid = (higherIdenx + lowerIndex)//2
      if arr[mid] == key:
        return mid
      elif arr[mid] > key:
        return binary_search(arr, lowerIndex, (mid-1), key)
      else:
        return binary_search(arr, (mid+1), higherIndex, key)
    else:
      return -1
      
  # iterative version
  def binary_search_iterative(arr, key):
    low = 0
    mid = len(arr)
    high = len(arr)
    
    while(high >= low):
      mid = (high + low) // 2
      if(arr[mid] == key):
        return mid
      elif (arr[mid] > key):
        high = mid-1
      else:
        low = mid+1
    
    return -1
  ```
  
- selection sort
  - sorting algorithm that treats the input as two parts: a sorted part and an unsorted part, and repeatedly selects the proper next value to move from the unsorted part to the end of the sorted part
  - Runtime: O(N^2)
  
```python
def selection_sort(arr):
    temp = 0
    for i in range(len(arr)):
        for j in range(i+1, len(arr)):
            if(arr[i] > arr[j]):
                temp = arr[i]
                arr[i] = arr[j]
                arr[j] = temp
    return arr
```

- insertion sort
  - sorting algo that treats inputs as two parts: a sorted part and unsorted part, and repeatedly inserts the next value from the unsorted part into the correct location in the sorted part
  - runtime: O(N^2)
    - for (full or nearly) sorted lists, runtime is O(N)
      - diff between selection sort here ^...insertion sort does not require iterating through each list member if nearly sorted or during sorting

```python
def insertion_sort(arr):
    # start from 1 because we assume at 0, list is sorted
    for i in range(1, len(arr)):
        j = i

        while j > 0 and arr[j] < arr[j - 1]:
            temp = arr[j]
            arr[j] = arr[j-1]
            arr[j-1] = temp
            j -= 1
    return arr
```

- shell sort
  - sorting algo that treats the input as a collection of interleaved lists, and sorts each list individually with a variant of the insertion sort algo
    - uses gap values to determine the number of interleaved lists (gap value of 3 means 3 interleaved lists)
    - gap value - positive integer representing the distance between elements in an interleaved list
      - for each interleaved list, if an element is at index i, the next element is at (index i + gap value)
  - begins by choosing a gap value `K` and sorting `K` interleaved lists in place and finishes by performing standard insertion sort on the entire array
    - ![image](https://user-images.githubusercontent.com/14286113/156668264-cb3a6b36-c46e-4100-8e27-5511afbb6177.png)
    - ![image](https://user-images.githubusercontent.com/14286113/156668334-3e8f0358-570e-49cf-ba95-9f3a4d14b774.png)
    - ![image](https://user-images.githubusercontent.com/14286113/156668372-ea1e2763-df33-470b-b293-cf1263ad3e9d.png)
  - shell sort requires less swaps than insertion sort
  - shell sort does not create interleaved lists, but rather sorts lists in place with insertion algos, doing `x+k` instead of `x+1`
  - performas well when choosing gap values in decending order (ex: powers of 2 -1)
  - shell sort sorts subsets of an input list
    - instead of comparing elements that are immediately adjacent to each other, the insertion sort variant compares elements that are at a fixed distance apart (aka gap space); this process repeats using different gap sizes and starting points within the input list
  - for small/ medium sized arrays, runtime is close to O(N) with best time (list is sorted) being O(n*logn) and worst being O(n*log^2n)
    -  faster than bubble and insertion sort
    -  various increment/ gap sequences can produce runtimes of On^2

```python
def inner_shell_sort(arr, start, gap):
    for i in range(start+gap, len(arr), gap):
        j = i
        while (j - gap >= start) and (arr[j] < arr[j-gap]):
            temp = arr[j]
            arr[j] = arr[j-gap]
            arr[j-gap] = temp
            j = j-gap

def shell_sort(arr, gap_values):
    for gap_value in gap_values:
        for i in range(gap_value):
            inner_shell_sort(arr, i, gap_value)
    return arr    
```

- quicksort
  - sorting algorithm that repeatedly partitions (based on a pivot) the input into low and high parts (each part unsorted), and then recursively sorts each of those parts
    - pivot - any value within the array being sorted, commonly the middle array element
      - all values in the low partition would be less than or equal to the pivot value
      - all values in the high partition would be greater than or equal to the pivot value
      - Runtime: O(NLogN)
        - Worst case O(N^2) but this is rare
  - ![image](https://user-images.githubusercontent.com/14286113/156682472-7d7aacc9-3f81-4cba-a59a-1d09f91f5b91.png)


```python
def partition(numbers, start_index, end_index):
    # Select the middle value as the pivot.
    midpoint = start_index + (end_index - start_index) // 2
    pivot = numbers[midpoint]
   
    # "low" and "high" start at the ends of the list segment
    # and move towards each other.
    low = start_index
    high = end_index
   
    done = False
    while not done:
        # Increment low while numbers[low] < pivot
        while numbers[low] < pivot:
            low = low + 1
      
        # Decrement high while pivot < numbers[high]
        while pivot < numbers[high]:
            high = high - 1
      
        # If low and high have crossed each other, the loop
        # is done. If not, the elements are swapped, low is
        # incremented and high is decremented.
        if low >= high:
            done = True
        else:
            temp = numbers[low]
            numbers[low] = numbers[high]
            numbers[high] = temp
            low = low + 1
            high = high - 1
   
    # "high" is the last index in the left segment.
    return high
 
def quicksort(numbers, start_index, end_index):
    # Only attempt to sort the list segment if there are
    # at least 2 elements
    if end_index <= start_index:
        return
          
    # Partition the list segment
    high = partition(numbers, start_index, end_index)

    # Recursively sort the left segment
    quicksort(numbers, start_index, high)

    # Recursively sort the right segment
    quicksort(numbers, high + 1, end_index)
    

# Main program to test the quicksort algorithm.
numbers = [12, 18, 3, 7, 32, 14, 91, 16, 8, 57]
print('UNSORTED:', numbers)

quicksort(numbers, 0, len(numbers)-1)
print('SORTED:', numbers)

# UNSORTED: [12, 18, 3, 7, 32, 14, 91, 16, 8, 57]
# SORTED: [3, 7, 8, 12, 14, 16, 18, 32, 57, 91]
```
- Merge sort
  - sorting algo that divides a list into two halves, recursively sorts each half, and then merges the sorted halves to produce a sorted list; the recursive partitioning continues until a list of 1 element is reached, as list of 1 element is already sorted
  - ![image](https://user-images.githubusercontent.com/14286113/156906388-f2024379-8616-4da4-98d9-dfb7fa1a447b.png)

  -  Runtime: O(NLogN)

```python
# numbers = arry containting the 2 sorted partitions to merge
# i = start index of the first sorted partition
# j = end index of the first sorted partiiton
# k = end index of the second sorted postion
def merge(numbers, i, j, k):
    merged_size = k - i + 1               # Size of merged partition
    merged_numbers = [0] * merged_size    # Dynamically allocates temporary array
                                          # for merged numbers
    merge_pos = 0                         # Position to insert merged number
    left_pos = i                          # Initialize left partition position
    right_pos = j + 1                     # Initialize right partition position
   
    # Add smallest element from left or right partition to merged numbers
    while left_pos <= j and right_pos <= k:
        if numbers[left_pos] <= numbers[right_pos]:
            merged_numbers[merge_pos] = numbers[left_pos]
            left_pos += 1
        else:
            merged_numbers[merge_pos] = numbers[right_pos]
            right_pos += 1
        merge_pos = merge_pos + 1
   
    # If left partition is not empty, add remaining elements to merged numbers
    while left_pos <= j:
        merged_numbers[merge_pos] = numbers[left_pos]
        left_pos += 1
        merge_pos += 1
   
    # If right partition is not empty, add remaining elements to merged numbers
    while right_pos <= k:
        merged_numbers[merge_pos] = numbers[right_pos]
        right_pos = right_pos + 1
        merge_pos = merge_pos + 1
   
    # Copy merge number back to numbers
    for merge_pos in range(merged_size):
        numbers[i + merge_pos] = merged_numbers[merge_pos]

# numbers = array containing the partition to sort
# i = start index of the partitiion to sort
# k = end index of the partition to sort
def merge_sort(numbers, i, k):
    j = 0

    if i < k:
        j = (i + k) // 2  # Find the midpoint in the partition

        # Recursively sort left and right partitions
        merge_sort(numbers, i, j)
        merge_sort(numbers, j + 1, k)
            
        # Merge left and right partition in sorted order
        merge(numbers, i, j, k)


# Create a list of unsorted values
numbers = [61, 76, 19, 4, 94, 32, 27, 83, 58]

# Print unsorted list
print('UNSORTED:', numbers)

# Initial call to merge_sort
merge_sort(numbers, 0, len(numbers) - 1)

# Print sorted list
print('SORTED:', numbers)
```

- Bucket sort
  - sorting algorithm that distributes numbers into buckets, sorts each bucket with an additional sorting algorithm, and then concatenates buckets together to build the sorted result
  - bucket - container for numerical values in a specific range
  - this sort algo is designed for arrays with non-negative numbers
  - the term "bucket sort" is used to refer to a category of sorting algos, instead of a specific sorting algo
    - refers to sorting algorithm that places numbers into buckets based on some common attribute, and then combines bucket contents to produce a sorted array 
  ![image](https://user-images.githubusercontent.com/14286113/156908372-94768ab2-ad7c-4d3a-a26d-354f4e8eb2c7.png)

- radix sort
  - bucket algo that is specifically for integers; it processed on digit at a time starting with the least signifcant digit and ending with the most significant
    - First, all array elements are placed into buckets based on the current digit's value
    - Then, the array is rebuilt by removing all elements from buckets, in order from lowest bucket to highest 
  - Runtime is O(N)
  - Ex: sorting based on second digit:
  ![image](https://user-images.githubusercontent.com/14286113/156908529-60ce8e41-a9f6-46d6-8178-4d32dfaa549a.png)

  - Ex: then sorting based on first digit:
  ![image](https://user-images.githubusercontent.com/14286113/156908548-3951c4a1-e2d7-4848-adab-4acf7658bf4d.png)

```python
# Returns the maximum length, in number of digits, out of all list elements 
def radix_get_max_length(numbers):
    max_digits = 0
    for num in numbers:
        digit_count = radix_get_length(num)
        if digit_count > max_digits:
            max_digits = digit_count
    return max_digits


# Returns the length, in number of digits, of value
def radix_get_length(value):
    if value == 0:
        return 1
   
    digits = 0
    while value != 0:
        digits += 1
        value = value // 10 
    return digits


def radix_sort(numbers):
    buckets = []
    for i in range(10):
       buckets.append([])

    # Find the max length, in number of digits
    max_digits = radix_get_max_length(numbers)
        
    pow_10 = 1
    for digit_index in range(max_digits):
        for num in numbers:
            bucket_index = (num // pow_10) % 10
            buckets[bucket_index].append(num)

        numbers.clear()
        for bucket in buckets:
            numbers.extend(bucket)
            bucket.clear()
      
        pow_10 = pow_10 * 10
   
    negatives = []
    non_negatives = []
    for num in numbers:
        if num < 0:
            negatives.append(num)
        else:
            non_negatives.append(num)
    negatives.reverse()
    numbers.clear()
    numbers.extend(negatives + non_negatives)


# Create a list of unsorted values
numbers = [47, 81, 13, 5, 38, 96, 51, 64]

# Print unsorted list
print('UNSORTED:', numbers)

# Call radix_sort to sort the list
radix_sort(numbers)

# Print sorted list
print('SORTED:', numbers)

# UNSORTED: [47, 81, 13, 5, 38, 96, 51, 64] 
# SORTED: [5, 13, 38, 47, 51, 64, 81, 96]
```

- bubble sort
  - sorting algo that iterates through a list, comparing and swapping adjacent elements if the second element is less than the first element
  - Runtime: O(N^2) due to nested loops
  - ![image](https://user-images.githubusercontent.com/14286113/156908936-2c8de9f7-8521-4c70-8b86-19ef79926844.png)

- quickselect
  - algo tht selects the Kth smallest element in a list (Ex: k=0 means return the first smallest element in the list)
  - for a list of N elements, quickselect uses quicksort's partition function to partition the list into a low partitition containing the X smallests elements and a high partition containig the N-X largests elemnts
    -   the Kth smallest element is in the low partition if K is <= the last index in the low parition and high partition otherwise
    -   quickselect is recursively called on the partition that contains the kth element; when a partition of size 1 is encountered, quickselect has found the kth smallest element
  - partially sorts the list
  - Runtime (best case and average): O(N)
  - Worst time (when sorting the entire list): O(N^2)
  - ![image](https://user-images.githubusercontent.com/14286113/156909382-9b31f673-2a79-4af7-945c-a4e5c2b39865.png)


- Overview of sorting algos

![image](https://user-images.githubusercontent.com/14286113/156908740-e7bf6f08-0d30-4e10-9cf0-a36139def4d9.png)
![image](https://user-images.githubusercontent.com/14286113/156908777-3b8f7862-5ecd-4c97-a4bc-7c63f50fb939.png)

## 12: Lists, Stacks, Queues

- positional list
  - list where elements contain pointers to the next and/or previous elements in the list

- singly-linked list
  - data structure for implementing a list ADT, where each node has data (value) and a pointer to the next node
  - type of positional list
  - Head: first node
  - Tail: last node
    - for a list with only one node, the head and tail are the same 
  - null: special vlaue indicating a pointer points to nothing
  - Ex of list: 
  ![image](https://user-images.githubusercontent.com/14286113/157033103-b958fc8a-2a86-4a12-89f9-3706640c385d.png)

  - Append operation
    - Inserts new node after the list's tail node
    ```python
    def append(list, newNode):
      if(list.head == null):
        list.head = newNode
        list.tail = newNode
      else:
        list.tail.next = newNode
        list.tail = newNode
    ```
    
  - Prepend operation
    - inserts new node before the list's head node
    ```python
    def prepend(list, newNode):
      if(list.head == null):
        list.head = newNode
        list.tail = newNode
      else:
        newNode.next = list.head
        list.head = newNode
    ```
    
  - Insert operation
    - inserts new node after a provided existing list node, *curNode*
    ```python
    def insert(list, curNode, newNode):
      if(list.head == null):
        list.head = newNode
        list.tail = newNode
      else if(curNode == list.tail):
        list.tail.next = newNode
        list.tail = newNode
      else:
        newNode.next = curNode.next
        curNode.next = newNode
    ```
    
  - Remove Operation
    - removes node after the specified list node, *curNode*
    ```python
    def remove(list, curNode):
      if(curNode == 0 and list.head != null:
        successorNode = list.head.next
        list.head = successorNode
        if(successorNode == null):
          list.tail = null
      elif(curNode.next != null):
        successorNode = curNode.next.next
        curNode.next = sucessorNode
        if(successorNode == null):
          list.tail = curNode
    ```
    
- node python implementation:

```python
class Node:
  def __init__(self, initial_data):
    self.data = intitial_data
    self.next = None
    self.prev = None
  
  # ex_node = Node(95) --> Creates node with a data value of 95
  
```

- python linkedList implementation:


```python
class LinkedList:
    def __init__(self):
        self.head = None
        self.tail = None

    def append(self, new_node):
        if self.head == None:
            self.head = new_node
            self.tail = new_node
        else:
            self.tail.next = new_node
            self.tail = new_node

    def prepend(self, new_node):
        if self.head == None:
            self.head = new_node
            self.tail = new_node
        else:
            new_node.next = self.head
            self.head = new_node

    def insert_after(self, current_node, new_node):
        if self.head == None:
            self.head = new_node
            self.tail = new_node
        elif current_node is self.tail:
            self.tail.next = new_node
            self.tail = new_node
        else:
            new_node.next = current_node.next
            current_node.next = new_node
   
    def remove_after(self, current_node):
        # Special case, remove head
        if (current_node == None) and (self.head != None):
            succeeding_node = self.head.next
            self.head = succeeding_node  
            if succeeding_node == None: # Remove last item
                self.tail = None
        elif current_node.next != None:
            succeeding_node = current_node.next.next
            current_node.next = succeeding_node
            if succeeding_node == None: # Remove tail
                self.tail = current_node
```

- doubly-linked list
  - data structure for implementing a list ADT, similiar to singly linked list where each node has data and two pointers: a pointer to the next node, and (unlike singly linked list) a pointer to the previous node
  - type of positional list
  
```python
class LinkedList:
    def __init__(self):
        self.head = None
        self.tail = None

    def append(self, new_node):
        if self.head == None:
            self.head = new_node
            self.tail = new_node
        else:
            self.tail.next = new_node
            new_node.prev = self.tail
            self.tail = new_node

    def prepend(self, new_node):
        if self.head == None:
            self.head = new_node
            self.tail = new_node
        else:
            new_node.next = self.head
            self.head.prev = new_node
            self.head = new_node


    def insert_after(self, current_node, new_node):
        if self.head is None:
            self.head = new_node
            self.tail = new_node
        elif current_node is self.tail:
            self.tail.next = new_node
            new_node.prev = self.tail
            self.tail = new_node
        else:
            successor_node = current_node.next
            new_node.next = successor_node
            new_node.prev = current_node
            current_node.next = new_node
            successor_node.prev = new_node
   
    def remove(self, current_node):
        successor_node = current_node.next
        predecessor_node = current_node.prev

        if successor_node is not None:
            successor_node.prev = predecessor_node

        if predecessor_node is not None:
            predecessor_node.next = successor_node

        if current_node is self.head:
            self.head = successor_node

        if current_node is self.tail:
            self.tail = predecessor_node
```

- Circular linked list
  - linked list where the tail node's next pointer points to the head of the list (start node), instead of null 
  - used to represent repeating processes
  - ![image](![image](https://user-images.githubusercontent.com/14286113/157063300-11acc6a7-fe09-4472-9879-fc5842cc549d.png)
  - Traversal works by terminating when reaching startNode (instead of null)

- Linked list traversal & search

```python

def traverseList(list):
  curNode = list.head
  
  while(curNode != None):
    # do some operation
    curNode = curNode.next

# supported by doubly linked list
def reverseTraverseList(list):
  curNode = list.tail
  
  while(curNode != null):
    # do some operation
    curNode = curNode.prev

def search(list, key):
  curNode = list.head
  
  while(curNode != null):
    if(curNode.data != null):
      return curNode
      
    curNode = curNode.next
    
  return null
    
 ```

- stack
  - ADT in which items are only inserted on or removed from the top of a stack (the first/ head element)
  - Can be implemented using linked list (co, array, or vector)
    - push uses linkedlist's prepend() 
    - pop uses linkedList's removeAfter(none) (or 0 for beginning of the list)
  - last-in first-out
  - Stack operations
  ![image](https://user-images.githubusercontent.com/14286113/157064922-9df71302-1c1c-44de-b5bf-9498ce0f1709.png)
 
```python
class Stack:
    def __init__(self):
        self.list = LinkedList()
        
    def push(self, new_item):
        self.list.prepend(new_item)    # Insert as list head (top of stack)
    
    def pop(self):
        popped_item = self.list.head   # Copy list head (top of stack)
        self.list.remove_after(None)   # Remove list head
        return popped_item             # Return popped item
```
  
- Queue
  - commonly implemented using linked list where list's head node represents queue's front and list's tail node represents the queue's end
  - pushing item means appending to the tail 
  - popping items means removing items from the head

```python
class Queue:
    def __init__(self):
        self.list = LinkedList()
        
    def push(self, new_item):
        self.list.append(new_item)     # Insert as list tail (end of queue)
    
    def pop(self):
        popped_item = self.list.head   # Copy list head (front of queue)
        self.list.remove_after(None)   # Remove list head
        return popped_item             # Return popped item
```

- Dequeue
  - ADT in which items can be inserted and removed at both the front and back (unlike Queue where items are inserted at the end, and removed from the front)
  - Operations
  ![image](https://user-images.githubusercontent.com/14286113/157111119-1749764c-4f8d-4596-9db7-b4c18dc09378.png)

- Sorting algos on linked lists
  - Insertion sort
    - Requires searching from head of the list for an element's insertion position (singly-linked list) whereas insertion sort operates similiarly to arrays for doubly linked lists since it has ability for backward traversal
  - Merge sort
    - Requires finding the middle of the list by searching linearly from the head of the list
  - Shell sort
    - cannot be done efficiently since requires jumping the gap between elements which can't be done in linked list (since each element between two elements must be traversed)
  - Quicksort
    - cannot be done efficiently (for singly linked list) since partitioning requires backward traversal through the right portion of the array and singly linked lists do not support this
  - Heap sort
    - cannot be done efficiently since indexes access is required to find child nodes in constant time when percolating down

- doubly linked list insertion sort

```python
def insertion_sort_doubly_linked(self):
    current_node = self.head.next
    while current_node != None:
        next_node = current_node.next
        search_node = current_node.prev
         
        while ((search_node != None) and 
               (search_node.data > current_node.data)):
            search_node = search_node.prev
      
        # Remove and re-insert curNode
        self.remove(current_node)
            
        if search_node == None:
            current_node.prev = None
            self.prepend(current_node)      
        else:
            self.insert_after(search_node, current_node)

        # Advance to next node
        current_node = next_node
```

- singly-linked list insertion sort

```python
def insertion_sort_singly_linked(self):
    before_current = self.head
    current_node = self.head.next
    while current_node != None:
        next_node = current_node.next
        position = self.find_insertion_position(current_node.data)
        if position == before_current:
            before_current = current_node
        else:
            self.remove_after(before_current)
            if position == None:
                self.prepend(current_node)
            else:
                self.insert_after(position, current_node)
        current_node = next_node

def find_insertion_position(self, data_value):
    position_a = None
    position_b = self.head
    while (position_b != None) and (data_value > position_b.data):
        position_a = position_b
        position_b = position_b.next
    return position_a
```

- Array-based lists
  - Since arrays have a fixed-size, array-based list implementations will dynamically allocate the array as needed as the number of elements changes

## 13 Hash Table

- Hash table
  - data structures that stores unordered items by mapping (or hashing) each item to a location in an array (or vector)
  - implemented using a Class with a list variable as a property
  - Advantage: searching, inserting, and removal is O(1)
    - possible by mapping item's key to an index that can be calculated with a hash function
  - hash function: computes bucket (hash table array elememnt) index from item's key
    - one hash function is using the module operator `%` to do `key % tableSize` to compute the bucket index
      - Ex: key % 20 will map keys to bucket indices 0 to 19
  - ![image](https://user-images.githubusercontent.com/14286113/157137663-d70c7590-308d-4910-b72b-3af75c583eb5.png)

- Collisions
  - occurs when an item being inserted into a hash table maps to the same bucket as an existing item in the hash table
  - handled by chaining or open addressing

- Open addressing
  - collision resolution technique where collisions are resolved by looking for an empty bucket elsewhere in the table

- Chaining
  - collision resolution technique where each bucket has a list of items so elements with the same computed bucket index will be stored in the bucket list, which may store multiple items that map to the same bucket
  - Removing/ Searching for items in hash table that uses chaining involves determining the bucket index and then searching the bucket list
  - a good hash function results in short bucket lists (for faster inserts, searches, and removes)

- Linear probing
  - a way to handle collisions by starting at key's mapped bucket and linearly searching the subsequent buckets until an empty bucket is found
  - inserts are done determinig bucket, then linearly probing each bucket for an empty one to insert the item
    - if reach last bucket, continue at bucket 0 until reaching the original bucket index...return 0 to indicate all buckets are occupied otherwise return true
  - search/ removal is done by probing each bucket until a matching item is found, an empty-since-start bucket is found, or all buckets have been probed
    - buckets that are marked empty-after-removal does not terminate the remove operation search
  - a good hash function will avoid hashing multiple items to consecutive buckets and thus minimize the average linear probing length to achieve fast inserts, searches, and removes
  
- Quadratic probing
  - handles collision by starting at the key's mapped bucket, and then quadratically searches subsequent buckets until an empty bucket is found
    - uses a quadratic formula for this

- double hashing
  - open-addressing collision resolution technique that uses 2 different hash functions to compute bucket indexes
    - uses a probing sequence to iterate through values of `i` to find an empty bucket

- mid-square hash function
  - squares the key, extracts R digits from the result's middle, and returns the remainder of the middle digits divided by hash table size N
  - the *base 2* implementation
    - is faster since it only requires few shift and bitwise operations

- multiplicative string hash function
  - repeatedly multiplies the hash value and adds the ASCII value of each character in the string;  A multiplicative hash function for strings starts with a large initial value. For each character, the hash function multiplies the current hash value by a multiplier (often prime) and adds the character's value. Finally, the function returns the remainder of the sum divided by the hash table size N.

- direct hash function
  - uses the item's key as the bucket index
  - direct access table: hash table with a direct hash function
  - limitations:
    - all keys must be postive even tho they may need to be negative for application
    - hash table size equals the largest key value, so it will be very large
  - advantage:  no collisions since each key is unique and gets unique bucket

## 14 Trees

- Binary tree
  - where each node has up to two children (left and right child)
  - leaf - a tree node with no children
  - internal node - a node with at least one child
  - parent - a node with a child 
  - root - one tree node with no parent; the top node
  - edge - link from a node to a child
  - depth - number of edges on the path from the root to the node
    - root node has depth of 0
  - level - nodes with same depth form a tree level
  - height - largest depth of any nodel its the max # of edges from root to any leaf
    - tree with one node has height of 0
    - height = log2N, where `N` is the number of nodes in a tree
    - operations are faster if height is small
    - random insertions keeps height near the minimum whereas inserting items in a nearly sorted order (root is small, to biggest) leads to nearly maximum tree height
      - nearly maximum height = N -1
    ![image](https://user-images.githubusercontent.com/14286113/157170144-dcb4c76f-496f-4523-abb2-83e741d97d13.png)

  - binary tree is full, if every node contains 0 or 2 children
  - binary tree is complete, if all levels, except possibly last level, are completely full and all nodes in the last level are as far left as possible
  - binary tree is perfect, if all internal nodes have 2 children and all leaf nodes are at the same level
  ![image](https://user-images.githubusercontent.com/14286113/157165556-e2775a18-1908-4417-ba42-eeeb9b5a0d95.png)

- binary search tree
  - form of binary tree that has an ordering property where any node's left subtree keys <= node's key, and right subtree's keys >= nodes key
  - duplicate values are allowed
  ![image](https://user-images.githubusercontent.com/14286113/157165845-96a457c5-65a1-40d3-841e-7cfc0f41fdad.png)

  -  search runtime
    -  O(H) where H is the tree height and tree height might be small as O(logN) for N number of nodes
    -  height can be kept minimized by keeping all levels full, except possibly at the last level; such a tree will have height of log2N
  -  ordering is smallest to largest
    -  smallest is the last left leaf node going up and down to the right most last leaf node
    -  ![image](https://user-images.githubusercontent.com/14286113/157166758-49c4be81-899f-4886-9130-a4e74843437d.png)
  -  BST search begins from tree root and traversing left or right downwards from there based on whether key is less than (go left) or greater than (go right) the node
    -  number of iterations for tree with N nodes is Log2N
  -  insert operations
    - inserts must obey BST ordering property
    - runtime is O(N) worst casea nd O(LogN) best case
  - remove operation
    - removes first-found matching node, restructuring the tree to preserve the BST ordering property
    - requires replacing found node with successor 
  - inorder traversal
    - this is where you visit all nodes in a BST from smallest to largest
    - requires starting at root, and recurively going down the left side to the right side

## 15: Heap

- max-heap
  - complete binary tree that maintains the simple property that a node's key is greater than or equal to the node's children's keys
  - max-heap's root is always the maximum key in the entire tree
  - max-heap with N nodes has height of logN
  - ![image](https://user-images.githubusercontent.com/14286113/157178151-b1e35452-6d53-4b84-9b68-5c5affe81476.png)
  
  - insert operation
    - starts by inserting node in tree's last level, and then swapping the node with its parent until no max-heap property violation occurs
    - does this by filling a level left to right before adding another level
      - therefore, tree's height is always the minimum possible
    - percolating: the upward movement of a node in a max-heap insert

  - remove operation
    - is always a removal of the root and is done by replacing the root with the last level's last node and swapping that node with its greatest child until no max-heap property violation occurs

- heap storage
  - heaps can be displayed in tree form, but they are stored in array form
  - array form is produced by traversing the tree's levels from left to right, and top to bottom
    - so root node would always be at index 0 in the array
    ![image](https://user-images.githubusercontent.com/14286113/157179128-9512474d-38af-40f4-9803-87f83a3599da.png)

- priority queue
  - a queue where each item has a priority, and items with higher priority are closer to the front of the queue than items with lower priority
  - push oepration inserts an item such that the item is closer to the front than all items of lower priority and closer to the end than all items of equal or higher priority
  - pop operation removes and returns the item at the front of the queue, that is the highest priority
  - commonly implemented with heaps as heap will keep the highest priority item in the root node and allow access in O(1) time and adding/ removing would be O(logN) worstcase

- heapsort
  - sorting algorithm that takes advantage of max-heap's properties by repeatedly removing the max and building a sorted array in reverse order
  - ![image](https://user-images.githubusercontent.com/14286113/157182125-ec6578f7-344f-4d3e-998b-13c3e1775012.png)
