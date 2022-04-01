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

