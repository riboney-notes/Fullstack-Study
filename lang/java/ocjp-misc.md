# Java SE 11 

## Intro

**Learnig Objectives**
*  OOP
*  Java syntax and coding conventions
* Java constructs and operators
* Core Java APIs
  * Collections
  * Streams
  * IO
  * Concurrency
* Deploying SE application

## 1. Introduction To Java

**Lesson objectives**
* Origins and use-cases
* Portablity and provider neutrality
* OO concetps
* Syntax and coding conventions
* Class with main method
* Compile & execute Java app

**Questions**
* How java works?
  * What is source code? What is the file extension
  * What is source code compiled into? What is the file extension of the compiled files?
  * Why is it compiled? How is it executed? (And how does JVM run the code?)
  * Discuss wora?
  * How is java code structured?
  * What does a class represent (attributes & operations)
  * What is an Object?
  * What does inheritance allow you to do? (reuse attributes/ operations across class hierarchy)
  * What does a superclass represent? (generic)
  * What does a subclass represent? (specific)
  * What can subclasses do for you? (define more specific attributes and behaviors)
  * How to restrict attributes/ methods from being inherited?
  * What package is responsible for collections?
  * What pacakge is responsible for System actions (sytem, object, class)
  * Is Java Case sensitive?
  * Package naming convention? (reverse company domain name + any naming system)
  * Class name (noun, mixed case)
  * Variable name (mixed case, lower capital at start)
    * Cant start with: numbers, underscore, or $
  * Constant name is uppercase with underscore separatng words
  * Method names are verbs and mixed case (starting with lower case)
  * Package and class name must form a unique combination
  * Packages are represented as folders where class files are saved
  * Syntax
    * all statements must end with semicolon
    * code blocks must be enclosed with {}
    * Are indentations required? (no)
  * How to access class in another package? (prefix class name with package name, use import)
  * Are imports present in compiled code? (no)
    * import statement has no effect at runtime efficiency of the class..just a simple convenience to avoid prefixing class name with package name through out source code
  * Access modifiers?
    * public
    * protected
    * default
    * private
  * Main method
    * what does it look like
    * Does the name must be `main`?
    * Explain each part
    * Does the name of the paremeter matter?
  * How to compile java classes on the command line
    * `javac` `-cp` `-d`
    * Since java 11, you can run a single source code as if it was a compile class (so no need to do `javac`, just do `java classname.java`)

**Task**
  * Create a 3 file java program
  * Compile to /bin folder
  * Run program, and pass multiple parameters (include space)

## 2. Primitive Types, Operators, and Flow Control Statements

**Lesson Objective**
* Describe primitive types
* Describe operators
* Explain primitive type casting
* Use `Math` class
* Implement flow control with `if/else` and `switch` statements
* Describe JShell

**Questions**
* How many primitive types? 8
  * 4 integral types: byte, short, int, long (char is also integral)
  * 2 float types: float (requires f on numeric literals) and double
  * boolean
  * char
* How do you represent values for the various types? How can the literals look?
  * Whole numbers:
    * Binary - 0b1001
    * Octal - 072
    * Decimal - 1234
    * Hex - 0x4F
  * Float numbers:
    * Normal: 123.3
    * Exponential notation: 1.2345E3
    * NOTE: remember, F (upper or lowercase) at the end for floats
  * Char:
    * normal: 'y'
    * unicode: '\101'
    * numbers: 3 (only single digit)
* Can char have more than 1 digit? NO, 'abc' is not valid...only single chars or unicodes
* is `True` or `true` or "f" valid for boolean type? NO, only true and false are
* How to define a long value? Put a upper or lowercase L at the end!
* What is the default value for boolean? false
* How do smaller types behave with bigger types? They get automatically promoted
  * You can assign variables of smaller types to variables of larger types
* If you do operations with 2 data types smaller than int, what is the data type of the result? Int
  * if doing operations with data type equal or bigger than int, what is the data type of the result? the type of the largest participant in the operation
* Can you assign a bigger type value to a smaller type? No, not without explicit casting
* given `byte a = 127, b = 5;` (btw is this valid (yes)), what is the result of `byte c = a+b` (error because a+b gets promoted to int, and int cant be stored into smaller type byte unless casted)
* What does a char literal look like? its a value surrounded by single quotation marks
* What happens when type overflows?
  * So for like `byte a = 127, b = 5`, `byte e = (byte) (a+b) = -124` Why? Because when type overflows (132 > 128), the value flips and goes into the opposite signed range
* Can you include char values in operations?  Yes, they are 16 bit values before int and after short
* what is the smallest type to biggest? byte > short > char > int > long > float > double
* how to get a float number out of a operation involving whole numbers? Cast at least one of the values to a float type, given `int a=127 b=5`
  * `float g = a/b // 25.0f`
  * `float g = (float)(a/b) // 25.0f`
  * `float g = (float)a/b // 25.4f`
* We know that adding data types smaller than int, will result in value that is int....to prevent this, you cast it to something other than int...is this casting necessary for unary operations? No
* How does MAth.round() behave? It will round to whole numbers, unless you explicity cast one of the paremters to float
  * How to use Math.round to get a decimal number with your chosen precision
* Binary number represenatation
  * Java uses two's complement implementation of signed magint...LOOK THIS UP
  * look up bitwise commplement operator
* Short-circut evaluation (&& and ||) - enables you to not evaluate the right-hand side of AND or OR operations when the overall result can be predicted from the lefthand side value
  * `& | ^` is full evaluation
* What are the types switch expression can be? byte, short, char, int, String, ennum
* What happens if you omit the break? Does the next case block execute?

## 3. Text, Date, Time, and Numeric Objects

**Lesson Objectives**
* Manipulate text values using String & StringBuilder Classes
* Describe primitive wrapper classes
* Perform string and primitive conversions
* Handle decimal numbers using BigDecimal Class
* Handle date and time values
* Describe localization and formatting classes

**Questions**
* Are strings immutable? Yes
* How to modify string? Stringbuilder
* Why use wrapper classes? Wrapper classes have methods
* Instant and Duration good for system tasks (ex: timestamps)
* Period moe suitable for business logic

**Tasks**
* Formatting currencies
* Dealing with time zones
* Dealing with time
* Using Resource bundles
* Using message format

## 4. Classes and Objects, Part 1

**Lesson Objectives**
* Model business problems using classes
* Defining instance methods and variables
* Describe the `this`
* Explain object instantiation
* Explain local variables and local variable type inference
* Explain static variables and methods
* Invoke methods and access varaibles
* Describe the Netbeans IDE

## 5. Class Design

**Lesson Objectives**
* Method overloading
* Constructors
* Encapsulation and immutability (explain it)
* Enums
* Explain parameter passing
* Explain memory allocation and cleanup
* Copy by value vs copy by reference

**Questions**
* when does intance initializer get called (before constructor)

**Task**
* Create immutable classes

## 6. Inheritance

**Objectives**
* Extend classes
* Reuse code through inheritance
* `instanceof` operator
* Describe `super`
* Subclass constructors
* Override superclass methods
* Explain polymorphism
* Abstract classes and methods
* Final classes and methods
* Override Object class methods

**Questions**
* Can you extend more than one class?
* IF you assign a subclass reference to a variable of a supertype, does the variable get to call subclass methods?
* Casting from generic type to specific and vice versa
* `this` and `super` and shadowing
* When do you have use super constructor in subclass constructor
* Class loading and initialization execution order (only loaded once)
  * Object class static initializer
  * Class static initializer
  * Subclass static initalizer
* Object instantiation execution order:
  * Object class constructor
  * Class instance initalizer
  * Class constructor
  * Subclass instance initalizer
  * Subclass constructor
* How are methods overrided in polymorphism
* How is access modifier treated when method is overridden
* When to use abstract class?
  * To describe something that shouldn't have a specific implementation; Ex: We don't buy products, we buy real items like banana, toy, etc
* What is equals and hashcode method
* Override equals and hashcode method
* What is String internment

**Task**
* Create Food & Drink that extends Product
* Make Product Abstract
* Create PRoductManager to provide factory methods that create instances of Food and Drink
* Test out casting and polymorphism
  * Try casting a Food to a Drink and vice versa


## 7. Interfaces

**Objectives**
* Describe interfaces
* Implement interfaces
* Describe nonabstract interface methods
* Explain generics
* Utilize common Java interfaces
* Implement composition design pattern

**Questions**
* What can kind concrete methods can interface contain?
* Can you have variables in interfaces? (only constants)
* What are instance methods access modifiers? (public and abstract)
* What is the multiple inheritance problem?
* What can a child class do to the access modifier of a method inherited from parent
* What is functional interface
* What is generics

**Tasks**
* Create classes, interfaces, and abstract classes with the same method name and try using that method
  * try it with static and default methods
* Implement comparable
* Use cloneable
* Design Ratable interface to enable rating for various objects
  * Design review class to contain information about Rating and review comments
  * Add logic to the ProductManager class to handle product reviews, format and print reports 

## Book

**Questions**
* Does name of file have to match the class name?  (yes)
* How many public classes can there be in one file (1)
* Can you have more than one class in a file (yeS)
* What are the valid main method's parameter list?
  * `String[] args` `String args[]` `String... args`
* You can launch single file java programs without javac
  * `java example.java`...if error, then no .class is created cuz its fully in memory
* What are packages (logical grouping for classes)
What package is automatically imported into every java class file? (`java.lang`)
* Can you import mehtods (no)
* Does wild card import bring in child classes (no)
* Specific import statements have more precedence over wildcard statements
  * If two import statements clash, then `ambigous` error is thrown
  * To solve this, use the fully qualified class name to specify a variable or thing
* By default javac command places the compiled classes in the same directory
  * use `-d` to place class files into a different directory
  * use `-cp` with java to specify classpath for java to find the classes
* Classpath commands: `-cp` `-classpath` `-class-path`
* Order of class elements is important
  * PIC = package, import, class
* Does java support operator overloading? (no)
* Ch1 Sumarry on p 29
* What makes a code block? (curly braces)
  * Outside of methods, they are instance initializers
    * Cannot exist inside methods
* Order of initialization
  * Fields and instance initializer blocks are run in the order in which they appear in the file
  * constructor runs after all fields and instance initializer blocks have run
* floats require letter f following the number (otherwise its just a double)
* byte holds value from -128 to 127
* `short` and `char` are both integral types with 16 bit length, except
  * short is signed (splits range across postiive and negative numbers)
  * char is unsigned and goes from 0 to 65k
* Number of bits of data types is used by Java to figure out how much memory to reserve for your variable
* literals are the direct value, not some variable or reference
  * numeric literals are read as `int`
    * to define as long, use numbers with `L` to denote its a long
  * you can define literals in other formats:
    * octal
    * hexadecimal
    * Binary
  * You can have underscores in numeric literals (in place of commas)
    * can't have it in the front or end of literal or before/ after a decimal
    * you can place multiple underscore characters next to each other
* Primitive types hold their values in the memory where the variable is allocated
  * references points to an object by storing the memory address where the object is located (pointer)
* reference types can be assigned `null` which means they don't point to any objects
  * primitives can't be assigned null, compiler error (use a wrapper class)
* variable is a name for a piece of memory that stores data and has a data type
* Identifier: name of a variable, method, class package, interface, etc
  * Must begin with a letter, $, or _
  * Can contain numbers, but not start with number
  * single underscore is not allowed as identifier
  * cant use identifier with same name as reserved key word
* How many variables can declare/ initialize in the same statement? Multiple given that they are of the same data type
* What is a local variable? Any variable defined within a constructor, method, or initializer block
* Do local variables have a default value? No, they must be initailized before use 
* Instance variables = fields; variable defined within a specific instance of an object; changing one instance varaible does not effect the other
* Class variables are defined on class level and is shared among all instances of the class
* Instance and class variables don't need to be initialized; they already have default variables
* `var` (local type inference) only works for local variables (not class or instance variables)
* var gets type from the value its assigned
  * var MUST be initialized on the same line it is declared
  * var can not be initialized with `null` (but can be assigned null afterwards, giving that the underlying data type of var is an object)
    * Note: `var o = (String)null;` is valid since type is provided
  *  method parameters can not be var type
  * only local variables can be var
  * is var allowed to be used as an identifier? YES, its not a reserved word
    * however it is a reserved type name....so it can't be used to define a type, class, interface, or enum
  * Each block of code defines its own scope
  * Inner scopes can reference variables defined in the outer scopes, but not vice versa
  * All java objects are stored in your program's memory heap
    * heap (aka free store) represents a large pool of unused memory allocated to java app
  * Garbage collection refers to the process of automatically free moemory on the heap by deleting objects that are no longer reachable in your program
    * "No longer reachable" - where an object has no reference pointing to it or all references to the object have gone out of scope
  * `System.gc()` triggers garbage collection but is not guranteed to run
  * Reference - variable that has a name and can be used to access the contents of an object
    * all reference are the same size, no matter wht their type is
  * Objects sits on the heap and does not have a name
    * no way to access an object except through reference
  * Object cannot be passed to a method or returned from a method
    * object gets garbage collected, not its reference
  `finalize()` can run zero or one times, not twice

**ch3**
* OPerator is special symbol that can be applied to a set of operands (variables, values, or literals) and that returns a result
* unary, binary, and ternary operators can be applied to one, two, or three operands
* Order of operator precedence
  1. Post-unary operator (x++, x--)
  2. Pre-unary operator (--x, ++x)
  3. Unary operators (-,!,~, +, (type-casting))
  4. Multi/ Div/ modulo (*,/,%)
  5. Add/minus (+,-)
  6. Shift operators <<,>>,>>>
  7. Relational (<, >, <=, >=, instanceof)
  8. Equal/ not equal to (==, !=)
  9. Logical operators (&, ^, |)
  10. Short circuit operators (&&, ||)
  11. Ternary operators
  12. Assignment operators  (=, +=, -=, *=, /=, %=, &=, ^=, |=, <<=, >>=, >>>=)
* No brackets allowed in arthimetic expression
* type casting operator must be on the LEFT side of operand
* compound
* cant use compound operator (ex: *=) without declaring/initializing variable first
* no need to explictiy cast a value (long g, int s, s *= g is valid no need to cast)
* is valid: if (health = true) (returns true and assigned health to true)
* `==` will automatically promote numeric data types if different
* Using `instanceof` with incompatible types throws compiliation error (only for classes, not interfaces)
* Doing `null instanceof ...` will always result in false
  * However, `null instanceof null` will throw compilation error
* Logical operators applied to numbers get referred to as bitwise opertors since the perform bitwise comparisons
* Logical truth rules
  * AND is only true if both operands are true
  * Inclusive OR is only false if both operands are false
  * Exclusive OR is only true if the operands are different
* Ternery expression
  * `booleanExpression ? expressionThatREturnsValue : expressionThatReturnsVAlue;`
  * Behaves like short circuit operators...only evaluates one side

**ch4**

* whitespace, tabs, indents are not evaluated as part of the execution
* Watch out for unreachable statements in if/else blocks
* switch requires `case` followed by vaue and colon
* switch requires parenthises round the swithc variable
* switch reqiures braces around the body
* || and | is valid, but only with the appropaite data types
* switch staetment is not required to contain any case statements
  * `switch (variable) {}` is valid
* switch variable data types
  * int, byte, short, char and their wrappers
  * no boolean, long, float, or double
  * enums
  * Strings
  * var (if the type resolves to a valid switch type)
* values in case statements must be
  * compile-time constant values of the same data type as the swithch value
  * so only literals, final cosntants, enum constans are lallowed
  * must be final values (marked final in the same expression it was declared)
  * cant have something that executes method at run time in case statement
    * So if a variable is initialized by a method (and even if that method is marked as final) it won't be valid for case statement
    * Methods can not be used as case statements, even if they are final
    * anything that is evaluated until runtime, is not valid as case statements
  * statements that are arithmetic operations (ex: 3*5) can be balid if they are able to be resolved at compile time and fit the swithc data type without an explicit cast
    * data types for `case` statements must match the data type of the `switch` variable
    * variables not marked as final cannot be used as case values, even if they are Strings (immutable) or objects
    * method parameters can't be used as case values, even if they are final
* omitting the `break` means all proceeding statements will be executed

* what is a loop? repetitive control structure that can execute a statement of code multiple times in succession
  * variables allow each repetition be different
* Loops
  * while loop executes 0 or more times
  * do while loop executes 1 or more times
* variable declared in the loop cannot be accessible outside of the loop
* in while and for loops, boolean condition is evaluated on every iteration of the loop, before loop executes
* all variables in the init block in for loop MUST BE SAME DATA TYPE
* Labels is an optional pointer to the head of a statement that allows the application flow to jump to it or break from it
  * Usuallly uppercase letters, with underscore between words
  * follows all basic rules of identifies
  * can be applied to if, switch statments, loops, and control and block statements
* `break` statement transfers flow of control out to the enclosing statement
  * can use break to the specified label (ex: break PARENT_LOOP)
* `continue` statement causes flow to finish the execution of the current loop; transfers control to the boolean exprssion tht determines if the loop should continue
  * it ends the current iteration of the loop instead of ending the loop altogether like with `break`
* Unreachable code is any code placed after `break, continue, and return`
  * will cause compiliation error
  * will cause error even if `break, continue, and return` is not executed or will never be executed....merely existing in the code will cause error
* Switch statements dont allow `continue` statement

## Misc tasks

* Ch4: Play around numerical casting in switch statements (switch variable short, case statements int....see when its valid or invalid)

-----

## Ch 5 Core Java APIs

**Concepts to know**
* Concatenation rules
  * If both operands are numeric, then numeric addition
  * If either operand is String, then concatenation
  * Expression is evaluated left to right
* String literal/ compile time constants
  * String pool
  * String equality
* How `Arrays.binarySearch` works
  * And how it gives you unpredicatable output if not sorted
* How `Arrays.compare` works
  * Return value types
  * How different values compare
  * How it requires same array type
* Arrays.mismatch()

**Questions**
* Are Strings immutable?
* Can immutable classes be subclassed?
  * No because they are final
* How to compare StringBuilders for equality?
* What is the difference between a String and a literal string?
  * "name" is literal...`name.toString()` returns a string, but is not a literal (so it does not go into string pool)
  * Strings that only computed at runtime, aren't literals
  * Has to be present at compile time
  * Only literals are stored in String pool
* Does concat (a += b) create a new String
  * Yes, and such is not saved into string pool
* What does an array look like in memory?
  * An area of memory on the heap with space for a designated number of elements

**Tasks**
* Do some string manipulation exercises
  * strip() (unicode white space)/ trim()
  * concat() substring() etc
* Use the Arrays class and manipulate/ play with arrays
  * Ex: find if arrays are same, find where array differs
* Create and play with  multidimensional arrays
  * asymmetric array too
* Play with array conversion to list and vice-versa
  * see if array is changed if list is changed
  * confirm fixed-size list vs immutable list
* How to create a arraylist from an array
* Use `Math` class methods

**Misc**
* Anonymous array
  * `int[] nums = {1,2,3}`
  * anoymous because type and size is not defined
* You can type `[]` before/ after the variable name..space is optional; These are valid:
```java
int[] a;   
int [] b;  
int []c;
int d[];
int e [];
```
* Array does not allocate space for String objects....instead it allocates space for a reference to where the objects are really stored

```java
String[] s = {"poop"};
Object[] o = s;
o[0] = new StringBuilder(); // compiles, but error at run-time
```

```java
String[] s = {"poop"};
Object[] o = s;
String[] s2 = (String[]) o;
s2[0] = new StringBuilder();  // Compiler error
```

* `compare()` return values
  * negative value mens first array is smaller than the second
  * zero means arrays are equal
  * postive nubmer means first array is larger than the second
* `int[] a [], b [][]` is valid and makes a 2D and 3D array

`var list = new ArrayList<>()` makes list be `ArrayList<Object>`
