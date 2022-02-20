# Java collections

## Defining and Iterating Collections

---

- All collection type classes inherit from `Collection`
- Diagram of Collection Interface hierarchy
    
    
    ![image](https://user-images.githubusercontent.com/14286113/154846184-b04f8dbc-dcfd-4243-8fd9-75d824dc2217.png)
    
    ![image](https://user-images.githubusercontent.com/14286113/154846214-2ecbf364-7c94-4a6d-a877-d00e36c5fa90.png)
    
    ![image](https://user-images.githubusercontent.com/14286113/154846228-295fb941-4dd5-46d2-b005-00d31932807f.png)

- The Collections API is divided into Interfaces and Implementations
    ![image](https://user-images.githubusercontent.com/14286113/154846255-ad284048-eaf9-4c76-8fb1-30347883dc03.png)

- Choosing a collection object
    ![image](https://user-images.githubusercontent.com/14286113/154846272-9f05fef6-0e10-4669-9608-8456c51a5955.png)
    
- What is an iterator
    - its like a "cursor" for the collection object that is used to go through the collection
- Why does the collection interface method `add` return a Boolean?
    - because of collections like Sets that only allow unique items to be added
        - if item to be added is not unique (fails the criteria for being added), then `add` returns a boolean to indicate failure to add & breaking rules for being added
- How to use iterator to loop through collection?
    - `while(objectIterator.hasNext()`
    - `objectIterator.next()`
- Why would you want to use iterator over a for loop?
    - so you can add or remove elements while you are iterating through the collection

## Collections with Iteration Order

---

- What is a list?
    - collection with iteration order
        
        ![image](https://user-images.githubusercontent.com/14286113/154846296-ade18939-de8f-4b5a-ad78-84bb7a1f22ba.png)

- List implementations
    - Arraylist
        - good for general purpose use
        - default choice
        - More CPU cache sympathetic
        - faster
        - resizes itself when gets closed to being filled
        
        ![image](https://user-images.githubusercontent.com/14286113/154846311-5e1a2f26-514e-479a-ad41-598e9dcace8e.png)

    - LinkedList
        - doubly linked list
            - each element has pointer to the next and previous element
        - Linked list keeps reference to the head and tail (first and last element of list)
        - Nature of linkedlists makes it very good for adding elements to list without needing to shuffle the entire list
            - with arraylist, you have to copy the entire list contents over and shuffle elements +1 when adding
        - Slower to iterate over linkedlist since it uses pointers (next and previous elements)
        - Worse for many operations
        - Good if adding many elements at start
            - or when adding/ removing lots of elements
        - expensive to get specific elements from linkedlist since it involves jumping from pointer to pointer
        
        ![image](https://user-images.githubusercontent.com/14286113/154846328-79a04fa2-9de9-4035-b05b-54a400cc3d2d.png)

    - Performance comparisons between Array and linked lists
        
        ![image](https://user-images.githubusercontent.com/14286113/154846343-8a0c4370-1a61-4237-bf06-ff503d7120b3.png)


## Collections with Uniqueness

---

- What are sets?
    - sets are collections of distinct elements
    - there are no duplicates
    - useful for keeping unique elements
- Hashset
    - implements SortedSet
    - Good general purpose implementation
    - resizes when it runs out of space
    - based upon hashmap
        - if you use hashset, you need to have hashcode method
        - calls hashcode() on element and looks up location
            - tip: let your IDE implement equals() and hashcode()
            - tip: can also use `Objects.hashcode(values,values,...);`
            - tip for equals: can use `Objects.equals(values,values,...)` which includes null checks as well
    - Equals - Hashcode contract
        - objectA.equals(objectB) —→ objectA.hashcode() == objectB.hashcode()
        - the contract is that if objA equals objB, then hashcode of objA must also equal hashcode of objB
        - so the implication is that when elements are added to hashset, their hashcodes are checked and if not equal, then element would be added
            - allows you to have unique instances of the same class to be stored in HashSet
        
        ![image](https://user-images.githubusercontent.com/14286113/154846365-7e878c39-68cd-4b86-8441-ba7c4e090fff.png)
        
    
- TreeSet
    - Based on TreeMap
        - uses a binary tree with a required sort order
        - tree has left and right node
            - depending on the sort order, you go left or right
    - Keeps elements in the given/ specified order
        - implements (SortedSet & NavigableSet)
        - elements must implement comparable, or treeset must have comparator, to define the sort order
- EnumSet
    - Only allows Enum objects to be stored (as keys?)
    - Specialized implementation for enums
        - uses a bitset based upon the ordinal of the enum
        - each enum has an ordinal number (0,1,2...) associated with it
- Algorithmic Performance
    
    ![image](https://user-images.githubusercontent.com/14286113/154846385-8ac78104-71f2-4a88-82b6-7d10195eb2fc.png)

- SortedSet & NavigableSet
    - enforce an order on the elements on the sets that implement these interfaces
    - not sorted by index
    
- SortedSet
    - tailSet and HeadSet are useful in getting all elements from one point to another
        - ex: get all light products to heaviestLight products
    
    ![image](https://user-images.githubusercontent.com/14286113/154846398-55e74de8-5043-42fd-a46f-0857b26fb0b6.png)

- NavigableSet
    ![image](https://user-images.githubusercontent.com/14286113/154846424-80be2f3d-0679-4c13-8e7c-29c81d1c4829.png)
    
