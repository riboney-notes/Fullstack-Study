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
  - data structure for implementing a list ADT, where each node has data and a pointer to the next node
  - type of positional list
  - Head: first node
  - Tail: last node
  - null: special vlaue indicating a pointer points to nothing


