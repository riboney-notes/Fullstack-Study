# OCP Oracle Certified Professional Java SE 17 Developer guide

_note to author: link to book is in kindle library_

## Ch 1 - Building Blocks

**_Objectives_**
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

- `main()` is the entry point of a java program
  - Ex:
  ```java
  public class MyClass {
    public static void main(String[] args){
      System.out.println("Hello World!");
      }
    }
  }
  
  // NOTE:
  //   To compile this, `javac MyClass.java` then `java MyClass`
  ```
  
 - Requirements of a `.java` file
   - No more than one public class
   - Filename must match the class name (case-sensitive) and must have `.java` extension
   - If it is the entry point of the program, it must have a valid `main()` method

### Package declarations and imports

- statement: instruction
- `import` statement: tell Java which packages to look in for classes
- Wildcard import is a shortcut that imports all the classes in a package
  - Ex: `import java.util.* // imports all classes in the util package`
  - it doesn't import child packages, fields, or methods...only imports classes directly under the package in the import statement
- `java.lang` package is a special pacakge that is always automatically imported
- Don't need to import a class if it is in the same package
