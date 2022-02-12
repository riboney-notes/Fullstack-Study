# Java SE 11 Developer 1Z0-819

## Exam Resources & Links
- Course: [Oracle's Java SE 11 Course (30 Hours)](https://education.oracle.com/software/java/pFamily_48)
- Java 11 Exam book:  [OCP Complete Study Guide](https://www.amazon.com/Oracle-Certified-Professional-Developer-Complete/dp/1119619130)
- Java 11 Practice Tests: [OCP Java 11 Practice Tests](https://www.amazon.com/gp/product/1119696135)
- Java 8 Exam Book (with questions, free): [good for practice maybe?](https://ocpj8.javastudyguide.com/)


## Exam topics

**Java Data types**
- [ ] Primitives
- [ ] Wrapper classes
- [ ] Operators
- [ ] Parentheses
- [ ] Type promotion
- [ ] Type Casting
- [ ] `String` class
- [ ] `StringBuilder` class
- [ ] Type inference

**Controlling Program Flow**
- [ ] Loops
- [ ] If/else
- [ ] Switch

**Java OOP**
- [ ] Java objects instantiation
- [ ] Nested Java objects instantiation
- [ ] Java object lifecycle
- [ ]    Object creation
- [ ]    Dereferencing by reassignment
- [ ]    Garbage collection
- [ ] Object fields
- [ ] Object methods
- [ ]    instance
- [ ]    static
- [ ]    overloaded
- [ ] Setters/ Getters
- [ ]    builders
- [ ] Variable scopes
- [ ] Encapsulation
- [ ] Immutablity
- [ ] Subclasses/ Superclasses
- [ ] Abstract classes
- [ ] Polymorphism/ casting
- [ ] Object type vs reference type
- [ ] Interfaces
- [ ]    functional interfaces
- [ ]    private methods
- [ ]    default methods
- [ ]    static methods
- [ ] Enums

**Exception handling**
- [ ] Try/ catch/ finally
- [ ] Try-with resource
- [ ] Multi-catch statements
- [ ] Custom Exceptions

**Collections**
- [ ] Generics
- [ ]    Wildcards
- [ ] Array
- [ ] Collections
- [ ]    List
- [ ]    Set
- [ ]    Map
- [ ]    Deque
- [ ]    Convenience methods
- [ ] Comparator and comparable interfaces
- [ ]    sorting collections

**Streams & Lambdas**
- [ ] Functional interfaces
- [ ] Lambda expressions
- [ ] Streams
- [ ]    Filter data
- [ ]    Transform data
- [ ]    Process data
- [ ] Decomposition 
- [ ] Reduction
- [ ] Groupiing
- [ ] Partitioning
- [ ] Seqeuential streams
- [ ] Parallel streams

**JPMS**
- [ ] Deploy modular app
- [ ] Execute modular app
- [ ] Expose modules
- [ ] Services

**Concurrency**
- [ ] Runnable
- [ ] Callable
- [ ] ExecutorService
- [ ] java.util.concurrent API
- [ ] worker threads
- [ ] Thread safe code
- [ ] Locking mechanisms

**Java I/O API**
- [ ] Read/ Write with I/O Streams
- [ ] Serialization/ deserializtion
- [ ] java.nio.file API

**Security**
- [ ] DOS
- [ ] Code Inejction
- [ ] Input validation
- [ ] Data integrity
- [ ] Resource access security

**JDBC**
- [ ] Connect to database
- [ ] SQL operations

**Localization**
- [ ] Locale
- [ ] Resource bundles
- [ ] Parsing/ formatting messages, dates, and numbers

**Annotations**
- [ ] Creating, appling, processing annotations


## Detailed objectives
**Java Basics**
- [ ] Describe Java
- [ ] Identify key java features
- [ ] Create Java program with a main class
- [ ] Compile and run Java program from CLI
- [ ] Create and import packages
- [ ] Declare and initialize variables (including casting and promoting data types)
- [ ] Identify scope of variables
- [ ] Use local variable type inference
- [ ] Create and manipulate Strings
- [ ] Manipulate data using StringBuilder class and methods
- [ ] Using operators & use parenthesis to override operator precedence
- [ ] Use java contol statements (if, else, switch)
- [ ] Use iterative statements (do/while, while, for, for each, break, continue)
- [ ] Use Enums

**Arrays**
- [ ] Declare, instantiate, and use 1D array
- [ ] Declare, instantiate, and use 2D array
- [ ] Use wrapper classes, autoboxing, and autounboxing
- [ ] Describe Collections framework
- [ ] Use the main Collection interfaces
- [ ] Use Comparator and Comparable interfaces
- [ ] Use convenience methods for collections

**OOP**
- [ ] Declare, instantiate, java objects
- [ ] Explain object lifecycles (creation, dereferencing by reeassignment, garbage collection)
- [ ] Define structure of Java class
- [ ] Setters and Getters for java fields
- [ ] Use methods and constructors with args and return values
- [ ] Use overloaded methods
- [ ] Distinguish overloading, overriding, and hiding
- [ ] Apply static keyword to fields and methods
- [ ] Apply access modifiers
- [ ] Apply encapsulation principles to a class
- [ ] Use subclasses and superclasses
- [ ] Use abstract classes
- [ ] Use interfaces
- [ ] Use default and private methods in interfaces
- [ ] Distinguish class inheritance, interface, and abstract classes
- [ ] Use final classes
- [ ] Use inner, nested, and anonymous classes
- [ ] Enable polymorphism by overriding methods
- [ ] Use polymorphism to cast and call methods
- [ ] Use polymorphism to differentiate object type and reference types


**Exceptions**
- [ ] Understand advantages of exception handling
- [ ] Differentiate among checked, unchecked exceptions, and Errors
- [ ] Create try-catch blocks
- [ ] Determine how exceptions alter program flow
- [ ] Throw exceptions
- [ ] Use try-with resources construct
- [ ] Use custom classes
- [ ] Test invariants by using assertions

**Functional Interfaces, lambda expresssions, and Stream API**
- [ ] Use Functional interfaces
- [ ] Use lambda expressions, statement lambdas, local-varaible for lambda parameters
- [ ] Describe Stream interface and pipelines
- [ ] Use method reference
- [ ] Use interfaces from `function` package
- [ ] Use core functional interfaces: PRedicate, COnsumer, Function, Supplier
- [ ] Use primitive and binary variations of base interfaces of function package
- [ ]  Extract stream data using map, peek, and flatMap methods
- [ ] Search stream data using findFirst, findAny, anyMatch, allMatch, and noneMatch methods
- [ ]  Use Optional class
- [ ] Perform calculations using count, max, min, average, and sum stream operations
- [ ] Sort a collection using lambda expressions
- [ ] Use Collectors with streams, including groupingBy and partitioningBy operations
- [ ] Use parallel streams
- [ ] Implement decomposition and reduction with streams

**Modules**
- [ ] Describe Modular JDK
- [ ] Declare modules and enable access between modules
- [ ] Describe how modular project is compiled and run
- [ ] Migrate apps from before JDK 9 to JDK 11
- [ ] Use jdeps to determine dependencies and identify ways to address cyclic dependencies
- [ ] Describe the components of Services including directives
- [ ] Design a service type, load services using SErviceLoader, check for dependencies of the services including consumer and provider modules

**Concurrency**
- [ ] Create worker threads using Runnable, Callable, and use an ExecutorSErvice to concurrently execute tasks
- [ ] Use concurrent collections and classes including CyclicBarrier and CopyOnWRiteArrayList
- [ ] Write thread-safe code
- [ ] IDentify threding problems such as deadlocks and livelocks

**I/O and NIO2**
- [ ] Read/ write data from/to console and file using I/O streams
- [ ] Read/write files with I/O streams
- [ ] Read/write objects by using serialization
- [ ] Use Path interface to operate on file and directory paths
- [ ] Use Files class to check, delete, copy, or move a file/directory
- [ ] Use Stream API with Files

**Secure coding**
- [ ] Prevent Denial of service
- [ ] Secure sensitive information
- [ ] Implement data integrity guidelines - injections and incusion and input validation
- [ ] Prevent external attack of the code by limitiing accessiblity, extensiblity properly handling input validation, and mutability
- [ ] Securely constructing sensitive objects
- [ ] Secure serialization and deserialization

**JDBC**
- [ ] COnnect to database using JDBC URLS and DriverManager
- [ ] Use PreparedStatement to perform CRUD operations
- [ ] Use PreparedStatement and CallableStatement APIS to perform DB operations

**Localization**
- [ ] Use the Locale class
- [ ] Use resource bundles
- [ ] Format messages, dates, and numbers 

**Annotations**
- [ ] Describe purpose of annotations and typical use cases
- [ ] Apply annotations to classes and methods
- [ ] Describe commonly used annotations in the JDK
- [ ] Create custom annotations

## Exam study plan

**WEEK 1: Mar  1 -  5**
* Day One
  * 1 - Introduction to Java
  * `Ch 1,2 (1-50)`: [Intro] [Basics]

* Day Two
  * 1 - Introduction to Java 
  * `Ch 2,3 (50-100)`: [Basics] [Operators]

* Day Three
  * 2 - Primitives, Operators, and Flow control
  * `Ch 3,4 (100-150)`: [Operators] [Decision structures]

* Day Four
  * 2 - Primitives, Operators, and Flow control
  * 3 - Text, Date, Time, and Numeric objects
  * `Ch 4,5 (150-200)`:[Decision structures] [Core API]

* Day Five
  * 3 - Text, Date, Time, and Numeric objects
  * `Ch 5,6,7 (200-250)`: [Core API] [Lambdas & Functional interfaces] [Methods & Encapsulation]

**WEEK 2: Mar  8 - 12**
* Day One
  * 4 - Classes and Objects
  * `Ch 7,8 (250-300)`: [Methods & Encapsulation] [Class Design]

* Day Two 
  * 4 - Classes and Objects
  * `Ch 8 (300-350)`: [Class Design]

* Day Three
  * 5 - Improved Class Design
  * `Ch 8,9 (350-400)`: [Class design] [Advanced class design]

* Day Four
  * 5 - Improved Class Design
  * 6 - Inheritance
  * `Ch 9,10 (400-450)`: [Advanced class design] [Exceptions]

* Day Five
  * 6 - Inheritance
  * `Ch 10,11 (450-500)`: [Exceptions] [Modules]

**WEEK 3: Mar 15 - 19**
* Day One
  * 7 - Interfaces
  * `Ch 13 (550-600)`: [Annotations]

* Day Two
  * 7 - Interfaces
  * `Ch 14 (600-650)`: [Generics & Collections]

* Day Three
  * 8 - Array and Loops
  * `Ch 14,15 (650-700)`: [Generics & Collections] [Functional Programming]

* Day Four
  * 8 - Array and Loops
  * 9 - Collections
  * `Ch 15,16 (700-750)`: [Functional programming] [Exceptions, assertions, and localization]

* Day Five
  * 9 - Collections
  * `Ch 16 (750-800)`: [Exceptions, assertions, and localization]

**WEEK 4: Mar 22 - 26**
* Day One
  * 10 - Nested Classes and Lambda Expressions
  * `Ch 17,18 (800-850)`: [Modular Applications] [Concurrency]

* Day Two
  * 10 - Nested Classes and Lambda Expressions
  * `Ch 18 (850-900)`: [Concurrency]
  
* Day Three
  * 11 - Java Streams API
  * `Ch 19 (900-950)`: [I/O]

* Day Four
  * 11 - Java Streams API
  * 12 - Exceptions
  * `Ch 19,20 (950-1000)`: [I/O] [NIO 2]

* Day Five
  * 12 - Exceptions
  * `Ch 20, 21 (1000-1050)`: [NIO 2] [JDBC]

**WEEK 5: Mar 29 -  2**
* Day One
  * 13 - Java IO
  * `Ch 21, 22 (1050-1100)`: [JDBC] [Security]

* Day Two
  * 13 - Java IO
  * `Ch 12 (500-550)`: [Java Fundementals]

* Day Three
  * 14 - Concurrency

* Day Four
  * 14 - Concurrency
  * 15 - Modules

* Day Five
  * 15 - Modules


**WEEK 6: Apr  1 -  5**
* Day One
  * 16 - Annotations

* Day Two
  * 17 - JDBC

* Day Three
  * 18 - Java Security

* Day Four
  * 19 - Advanced Generics

* Day Five
  * Review

**WEEK 7: Apr  5 -  9**
* Day One
  * Data Types Test
  * Program Flow Test
  * OOP Test

* Day Two
  * Exception Handling Test
  * Arrays and Collection Test

* Day Three
  * Steams & Lambdas Test
  * JPMS Test

* Day Four
  * Concurrency Test

* Day Five
  * Java I/O Test

**WEEK 8: Apr 12 - 16**
* Day One
  * Security Test
  * JDBC Test

* Day Two
  * Localizationn Test

* Day Three
  * Annotation Test
  * Practice Exam 1

* Day Four
  * Practice Exam 2

* Day Five
  * Practice Exam 3

**WEEK 9: Apr 19 - 23**
* Day One
* Day Two
* Day Three
* Day Four
* Day Five
