# Data Structures And Algorithm Analysis in C++

[link](https://www.pearson.com/us/higher-education/program/Weiss-Data-Structures-and-Algorithm-Analysis-in-C-4th-Edition/PGM148299.html)

## CH 1: Programming: A General Overview

### 1.2 Mathematics Review

<details><summary>Exponents</summary>
  
  ![image](https://user-images.githubusercontent.com/14286113/161382403-7a445711-eb01-483e-bbb2-9319a26b5d30.png)

</details>

<details><summary>Logarithms</summary>
  
  ![image](https://user-images.githubusercontent.com/14286113/161382488-cd5ab872-cb80-4cfb-94e9-a961503746cb.png)

</details>

<details><summary>Geometric Series</summary>

  ![image](https://user-images.githubusercontent.com/14286113/161382601-7a8d3a0f-60d3-4007-afcf-7fcab1854846.png)

</details>

<details><summary>Arithmetic Series</summary>

  ![image](https://user-images.githubusercontent.com/14286113/161382680-ff553444-d2bc-4f3b-b057-3a6ea31f00e7.png)

</details>

<details><summary></summary>

</details>

*TODO: Skipped some sections...include them in notes later*

### 1.3 Intro to Recursion

- Recursive
  - describes a function that is defined in terms of itself
- Base case
  - value for which the recursive function is directly known without resorting to recursion
- Fundamental Rules of Recursion:
  1. Base cases: Must feature base cases which can be solved without invoking recursive calls
  2. Making progress: Recursive calls must always be to a case that makes progress toward a base case
  3. Design rule: Assume all recursive calls work
  4. Compound interest rule: Never duplicate work by solving the same instance of a problem in separate recursive calls

### 1.4 C++ Classes (p 12)

**Example C++ class**

```cpp
class IntCell
{
  public:
    // default parameter for constructor
    // intalization list (`:storedValue {intialValue}`)
    // explict allows you to avoid behind the scenes type conversions
    //    otherwise, `IntCell example = 37;` would be allowed because a one-paremeter constructor defines
    //    an implicit type conversion where the compiler attempts to convert the right-hand side value to the
    //    IntCell type
    //      explict prevents this behavior
    explicit IntCell( int initialValue = 0 ) :storedValue { intialValue } {}
    
    // marking function as const to explicitly definte it as an accessor
    // by default, all class functions are mutators
    // mutator function cannot be applied to constant objects
    // so we use const to mark a function as not a mutator
    // if the implementation of this function changes state, then compiler would throw an error
    int read() const 
    {
      return storedValue;
    }
    
    void write (int x) 
    {
      storedValue = x;
    }
    
  private:
    int storedValue;
}
```

**C++ Class interface example**

```cpp
// interfaces are placed in a file that ends with `.h`
// IntCell class would need to #include this interface header file
// the definitions below (#ifdef...) uses preprocessor to prevent interface from being read twice in the course of compilation
#ifndef IntCell_H
#define IntCell_H

class IntCell
{
  public:
    explicit IntCell(int intitialValue = 0);
    int read() const;
    void write(int x);
    
  private:
    int storedValue;
};

#endif
```

**Example of class implementing interface**

```cpp
#include "IntCell.h"

// the `::` is scope resolution operator
// each member function must identify the class that it is part of
//    otherwise, it is assumed that the function is in global scope
// Syntax: `ClassName::memberName`
IntCell::IntCell( int initialValue ) : storedValue{initialValue} {}

int IntCell::read() const
{
  return storedValue;
}

void IntCell::write(int x )
{
  storedValue = x;
}

```

**CPP main class example that uses the previous two code snippets**

```cpp
#include <iostream>
#include "IntCell.s"
using namespace std;

int main()
{
  IntCell m;
  
  m.write(5);
  cout << "Cell contents: " << m.read() << endl;
  
  return 0;
  
  // notes below
  
  // valid class object declaration
  IntCell obj1; // zero parameter constructor
  IntCell obj2 { 12 }; // one paremeter constructor
  IntCell obj3{}; // zero parameter constructor
  IntCell obj4(); // error...not sure why tho
}
```

**`vector` and `string`**

- `vector` and `string` classes are intended to replace built-in C++ array and strings 
- _code examples and details for vector and string is skipped...refer to pg 19-20 for examples_

### 1.5 C++ Details

**pointers**
- pointer variable stores the address where another object resides
- ex:

```cpp
int main()
{
  // the * marks m as a pointer variable
  // the line below means that `m` is allowed to point to a IntCell object
  // m's value is the address of the object it points at
  IntCell *m;
  
  // intialize m to hold the address of the new IntCell() object
  m = new IntCell{0};
  // -> is used to refer to the IntCell `write()` member function
  m->write(5);
  cout << "Cell contents: " << m->read() << endl;
  
  // prevents memory leak by removing it from memory
  delete m;
  return 0;
}
```

**Dynamic object creation**
- `new` returns a pointer to the newly created object
  - ex: `m = new IntCell();`
  - ex: `m = new IntCell{};`
  - ex: `m = new IntCell;`

**Garbage collection and delete**
- C++ does not have garbage collection
- Objects allocated by `new` must be deleted when no longer referenced to prevent memory leaks
  - memory leaks - memory that is consumed by the program that is not being used
- Memory can be automatically reclaimed if variable is "automatic" or "local"
  - otherwise, `delete` operator must be used

**Assignment and comparison of pointers**
- assignment and comparison with pointers is based on the address values that pointers hold
- two pointer variables are equal if they point to the same object

**Accessing members of an object through a pointer**
- if pointer variable points at an object of a class type, then public members of the class can be referenced via the `->` operator

**Address-of operator (&)**
- this operator returns the memory location where an object resides
- useful for implementing an alias test (this is discussed elsewhere on the document)

**Lvalues, Rvalues, and references**
- lvalue is an expression that identifies a non-temporary object
  - ex: `string str = "foo"; // str is a lvalue`
- rvalue is an expression that identifies a temporary object is a value not associated with any object (ex: literal constant)
  - ex: `string str = "foo"; // "foo" is a rvalue` 
- result of a function or operator call can be an lvalue or rvalue, which can be specified in the return type
  - reference type allows you to define a new name for an existing value
- lvalue reference is declared by placing an `&` after some type
  - ex: `string str = "hell"; string & rstr = str; rstr += 'o'; //str and rstr is now "hello"...&str == &rstr // true, they are the same objects`
- rvalue reference is declared by placing an `&&` after some type
  - ex: _skipped_

**Uses for lvalue references**
- renaming an object that is known by a complicated expression
  - ex: `auto & whichList = theLists[ myHash(x, theLists.size() )]; //whichList can be used in place of the complicated expression`
  - if we omitted the `&` here, then only a copy would be made...not a reference

- range for statement
  - normal for loop, ex:
  ```cpp
  for(int i = 0; i < arr.size(); ++i) ++arr[i];
  ```
  - range for loop, ex:
  ```cpp
  for (auto & x : arr) ++x;
  ```

- avoiding copies
  - when you only need a value then its more effiecent to get a reference to the value directly rather than make a copy of it
    - ex: `auto x = findMax(arr); // makes a copy of the largest value and stores it in x`
    - ex: `auto & x = findMax(arr); // x is a reference to the largest value; largest value is not copied`

**Parameter passing**
- languages like C and java do call-by-value, which means that arguments to functions are copied into function parameter
  - these leaves the original arguments to be unchanged when the function modifies its parameters that are based on the arguments
- C++ allows you to pass parameters in different ways (along with call-by-value)
  - call-by-reference
    - AKA call-by-lvalue-reference
    - ex: `void swap(double & a, double & b); // calls like swap(x,y) would affect the actual x and y variables`
  - call-by-reference-to-a-constant
    - AKA call-by-constant reference
    - this is where do call-by-value except you restrict any modifications to the argument
    - ex: `string randomItem( const vector<string> & arr); // returns a random item in arr`
  - call-by-rvalue-reference
    - this is where you do a `mov` instead of a copy
    - due to the nature of rvalues being temporary, expressions such as `x=rval` where `rval` is a rvalue, are implemented using a move instead of a copy...which is more effiecient for performance
    - ex: `string randomItem( vector<string> && arr);`
- when to use the different types of parameter passing:
  - Call-by-value: good for small objects that should not be altered by the function
  - Call-by-constant: appropriate for large objects that should not be altered by the function and are expensive to copy
  - Call-by-reference: appropriate for all objects that may be altered by the function

**Return Passing**
- return-by-value: where fucntion returns an object of an appropriate type that can be used by the caller
  - result is usually an rvalue
- _skipped cuz i didnt really understand it_

_rest of the chapter skipped lol...ill come back to it later_

## CH 2 Algorithmn Analysis


<details><summary>placeholder, don't delete</summary>

</details>
