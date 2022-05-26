# OCP Oracle Certified Professional Java SE 17 Developer guide

_note to author: link to book is in kindle library_

## Ch 1 - Building Blocks

**Objectives**
- Handling date, time, text, numeric, and boolean values
  - primitives, wrapper classes, Math API, parentheses, type promotion, casting
- OOP approach
  -  declaring/ instantiating objects, nested objects, object life cycle, garbage collection, reassigning references
  -  Variable scopes, local variable type inference, encapsulation, immutable objects
  
### Environment

- JRE
  - Java Runtime Environment
  - subset of JDK that was used for running a program but could not compile one
  - Can be supplied as an executable
- JDK 
  - Java Development Kit
  - contains the minimum software needed to do java development
  - new version every 6 months
  - `javac` - command that converts .`java` source code files into `class` bytecode
  - `java` - command that launches the Java Virtual Machine (JVM) and runs the bytecode to execute java program
  - `jar` - command that packages files together
  - `javadoc` - command that generates documentation

### Class structure

- object: runtime instance of a class in memory
- reference: variable that points to an object
- methods: functions that are members of a class
- fields: variables that are members of a class 

- Example of a simple class

```java
public class MyClass {
  String name;
  
  public String getName(){ return name; }
  public void setName(String newName) { name = newName; }
}
```

- top-level type: data structure that can be definied independently within a source file
  - most top-level types are the `class` in java files
  - most are public, but this is not required
  - multiple top-level types can be present in the same file, but only one can be `public`
    - Ex:
    ```java
    public class MyClass {}
    class MyClass2 {}
    ```
 
### `main()` method
