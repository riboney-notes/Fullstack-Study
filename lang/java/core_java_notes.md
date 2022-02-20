# Chapter 6 Interfaces, Lambdas, inner classes

## Interfaces

---

- p 380 - 411
- Interface is like a contract for classes to follow; this allows you to program to interfaces & supertypes by being able use objects that implement interface as arguments
- Example of `compareTo` method (overrides method in Comparable class)
    
    ```java
    // Does not use generics
    public int compareTo(Object otherObject){
    	Employee other = (Employee) otherObject;
    	return Double.compare(salary, other.salary); // Double.compare will return negative
    																							// if first arg < 2nd arg, 0 if equal
    																						  // and positive if otherwise
    ```
    
    - Note: it doesn't matter what the negative or postive *value* is; all that it matters is that negative means less than, postive means great than....and 0 means equal
        - so you can do a subtraction operation like `id - [other.id](http://other.id)` when comparing int id values
        - However! this does not work for floating-point numbers; it is better to use `Double.compare(x,y)` instead
- `compareTo` method should be compatible with which method?
    - it should be compatible with the `equals` method such that when `x.equals(y)`, `x.compareTo(y)` should be exactly 0
        - Exception to this rule is `BigDecimal` since "1.00" and "1.0" are not equal but in `compareTo()` it would return 0
- Discuss antisymmetry rule
    - According to the library, `x.compareTo(y)` must equal `-sgn(y.compareTo(x))`
        - this means that if you flip the parameters of `compareTo`, the sign (but not necessarily the actual value) of the result must also flip
    - This causes problems when inheritance is used
        - Imagine `Manager` extends `Employee`
            - Since it extends, it implements `Comparable<Employee>` rather than `Comparable<Manager>`
            - if `Manager` chooses to override superclass's `compareTo`, then it must compare managers to employees
            - However! that would mean you need to make employee object cast to a `Manager`
                - Example
                    
                    ```java
                    public int compareTo(Employee other)
                    {
                    	Manager otherManager = (Manager) other; // NO
                    }
                    ```
                    
            - This violates the `antisymmetry` rule, If x is an `Employee` and y is a `Manager`, then `x.compareTo(y)` is ok because Manager can be cast to employee
                - but the reverse `y.compareTo(x)` throws a `ClassCastException`
        - This situation also is the same with `equals` (as is the solution)
        - Three solutions
            - if subclasses have different notions of comparisons, then you should outlaw comparison of objects that belong to different classes
                - Example (logic test to implement the above ^)
                    
                    `if(getClass() != other.getClass()) throw new ClassCastException();`
                    
            - if there is a common algorithm for comparing subclass objects, simply provide a single `compareTo` method in the superclass and declare it as `final` (so its not overidden by subclass)
            - if you want to compare subclasses, and want some objects (like `Manager` objects) to be great than others (like `Secretary` objects), then establish a pecking order, supply a method such as `rank`, and implement a single `compareTo` method that takes the rank values into account
- Can you subclass interfaces?
    - yes, just extend interfaces like you would with classes
- What are some other ways interfaces can be used (other than the normal way)
    - can be used to define constants
    - Ex: `Direction.NORTH, Direction.SOUTH, etc`
        - not recommended
- What are some things allowed in interfaces after JDK 8?
    - static methods are allowed
        - this is why the `Paths` library is no longer necessary since all the companion classes and methods are now just defined in the `Path` interfaces
        - So when interfaces are implemented, no reason to provide a separate companion class for utility methods
    - As of JDK 9, methods can be private
        - private methods can be static or not static (instance)
            - however their use is limited to only being helper methods for the other methods of the interfaces
    - default methods can be supplied to provide default implementation for any interface method
        - Ex: `default int compareTo(T other) { return 0;}`
        - some uses of default methods are:
            - useful in the case of `Iterator` that uses default for `remove` method when iterator is read-only
            - default method can be used to call other methods (like convience methods)
            - see p 394 for more detauls
- What is interface evolution
    - when you add methods to interface later, you run the risk of having older classes that implement that interface, fail to compile since they don't override that new method
        - adding a nondefault method to an interface is not source-compatible
        - even if you don't recompile the class, it will throw `AbstractMethodError` if you call the new method on the class
    - providing `default` method solves this
- When does a default method conflict arise?
    - happens if the same exact method is defined as a default method in one interface and then again as a method of a superclass or another interface
- What are the general guidelines on resolving default method conflicts
    - Superclasses win; Concrete methods from superclasses are used and default methods with the same name and paremter types are ignored
    - intefaces clash; if an interface provdes a default method and another interface contains a method with the same name & parameter types (default or not), then you must resolve the conflict by overidding that method
        - when a class that implements interfaces with conflicting methods, then you have to choose on of the two conflicting methods by specfying the interface name when calling the method
            - Ex: `Person.super.getName()`
- What is the callback pattern and what are some examples of it
    - pattern where you specify the action that should occur whenever a particular event happens
        - Ex: when you want an action to occur when a button is clicked or menu item is selected
- What is the `Comparator` interface
    - `Comparable` allows you to define the natural ordering of objects
    - `Comparator` has a `compare` method and classes that override this can be used to provide custom ordering like based on alphabetical, length, etc
        - just plug in an object that implements `Comparator` into a Arrays.sort method or smth
- What is object cloning
    - its where a class implements the `Cloneable` interface and overrides the `clone()` method to copy fields of `this` object and return a "copy` of that object (returns another object instead of a reference to `this` object)
        - Clone is simple for primitive values (you just do field-by-field copying)
            - however if you have fields that are objects, then its just copying the references to those subobjects instead of cloning them (shallow copy)
- When does it matter if a copy is *shallow*
    - if the attributes of the copy and original consist of primitives and immutable objects (ex: String) or if the subobject is effectively immutable (no mutators or references to it)
- What are marker/ tagging interfaces?
    - an interface with no methods; its only purpose is to allow use of `instanceof` inquiries
        - Ex: `if(obj instanceof Cloneable)`

## Lambda Expressions

---

- p 411 - 434
- What is lambda expression?
    - its a block of code that you can pass around so it can be executed later, once or multiple times
        - Example, lets say an object contains a method you would want to execute
        - Instead of passing around that object in order to execute that code, just pass around that method
    - Ex: `(String frist, String second) -> first.length() - second.length();`
        - another ex
            
            ```java
            (String first, String second) ->
            	{
            		if(first.length() < second.length()) return -1;
            		else if (first.length() > second.length()) return 1;
            		else return 0;
            	}
            
            ```
            
        
- What are functional interfaces?
    - Interfaces that have a single abstract method
        - lambda expression can be used whenever an object of an interface with a single abstract method is specified (lambda expression can be used to provide the implementation of that method, without having to create that object to call that method)
- What package defines a number of very good generic functional interfaces?
    - `java.util.function` package
    - `Supplier` used for lazy evaluation; to get objects when needed (with the `T get()` method)
    - `Predicate` used for passing a boolean function `boolean test(T t)`
- What is method reference?
    - something like `System.out::println` that directs the compiler to produce an instance of a functional interface, overriding the single abstract method of the interface to call the given method
        - vs: `new Timer(1000, event -> System.out.println(event))`
  <details><summary>Note</summary>
  
  ![image](https://user-images.githubusercontent.com/14286113/154846745-54a2adb7-9566-4627-afd0-95793c688813.png)

  </details>
                
- Syntax of method reference, and their variants?
    - the `::` operator separates the method name from the name of an object or class
    - object :: instanceMethod
        - ex: `System.out::println`
        - equivalent to a lambda expresssion whose parameters are passed to the method
            - `x -> System.out.println(x);`
    - Class :: instanceMethod
        - ex: `String:: compareToIgnoreCase` same as `(x,y) -> x.compareToIgnoreCase(y)`
        - first paremeter becomes the implicit parameter of the method
    - Class :: instanceMethod
<details>
  <summary>more method reference examples on p 421</summary>
  
  - example 
  
  ![image](https://user-images.githubusercontent.com/14286113/154846785-fcce7519-198a-4596-b8ab-19807e228a35.png)
  
  - example #2
  
  ![image](https://user-images.githubusercontent.com/14286113/154847125-4f9eaab2-3463-4886-89c6-23a6b6557125.png)
</details>

- Whats a good way to test if elements of a list are null?
    
    ```java
    list.removeIf(Objects::isNull);
    ```
    
- How to construct an array of a generic type T?
    - 
- What are the three "ingredients" of lambda expressions?
    - block of code or logic
    - parameters
    - values for free variables (varaibles that are not parameters and not defined inside the block)
        - these values are "captured" by the lambda expression
            - essentially this is done by copying free vraibles into the instance variables of the lambda expression (if it was an object)
            - NOTE: value must be one that doesn't change
            - Any captured variable must be effectively final
- What is closure?
    - block of code together with the values of free variables
    - Where lambda expression captures the value of a variable in the enclosing scope
    - NOTE: must be immutable values and you cant mutate the variables
        - ex:
            
            ```java
            public static void countDown(int start, int delay)
            	{
            		ActionListener listener = event ->
            		{
            			start--; // ERROR: Can't mutate captured variable
            			System.out.println(start);
            		};
            		new Timer(delay, listener).start();
            	}
            ```
            
    
- What is an effectively final variable
    - a variable that is never assigned a new value after it has been initialized
- What is the point of using lambdas?
    - deferred execution; some reasons:
        - running the code in a separate thread
        - running the code multiple times
        - running the code at the right point in an algorithm (ex: comparision operation in sorting)
        - running the code when something happens (button click)
        - running the code only when necessary
    - p 429 provides a great example of picking a functional interface in order to create a method for lambda expression
- Whats a convenient way for creating comparators?
    - Using the `Comparator` static methods such as `comparing()`
    - you can chain comparators with the `thenComparing()`
    - see p 433 for more information

## Inner Classes

---

- p 434 - 456
- Why would you want to use inner classes?
    - inner classes can be hidden from other classes in the same package
    - inner class methods can access the data from the scope in which they are defined - including the data that would otherwise be private
        - so gets access to both its own data fields and those of the outer object creating it
    - Implementing callbacks (although this has been replaced by lambdas)
    - Inner classes are genuinely more powerful than regular classes because they have more access privelages
- Syntax rules for inner classes
    - p 440
- Inner classes can cause security risk?
    - see p 443
- Local inner classes?
    - Yes! you can define a class *locally in a single method*
  <details><summary>Example</summary>
    
    ![image](https://user-images.githubusercontent.com/14286113/154847374-445ffa0b-4d72-4129-ba6d-bdbeb80d56b8.png)
  </details>
        
    - they can access the fields of their outer classes *and* access local variables (must be effectively final)
- Anonymous inner classes?
    - local inner class without a name
    - Essentially used whe you want to make only a single object of the class
- When should you use a static inner class?
