# Java OCJP Book

## CH 6 Lambdas and interfaces

**Concepts**
* Lambda variable scope
  * local
  * method
  * instance
  * static
* Lambda effectively final scopes
  * local and method need to be effectively final
  * instance and static don't need to be (maybe cuz its stored on the heap)

**Questions**

**Misc**

**Task**
* Play around with comparator and compareTo and see what the sorting order is
* Use Java API and lambdas (removeIf, sort, for each, binSonsumer for maps, etc)
* Review CH6 and update notes: concepts and questions

## CH 7 Methods and Encapsulation

**Concepts**
* Method declaration rules (ex: modifier before return type)
* varargs rules
* `protected` does not work for the very class it is referring to (or somthing)
* Static is called by the type....not instance
* Static can't refer to instance stuff
* `final` primitives vs objects
* `final` variables requiring to be initialzed
* when to use static or instance initilizers
* "pass-by-value"

**Questions**
* What is the method signature?
* What are the different access modifiers and their descriptions?
* Can you omit the return type in a method?
* If method has a return type, can you omit the `return` keyword in the method body?
* Can you use an instance to call a static variable/ method?
* If the instance is set to null, can you still call the static variable/ method?
* What is method overloading?
* How overloading works with generics and type erasure
* How overloadig works with arrays of primiitve and wrapper type
* The order in which overlaoded method is invoked bsed on argment


**Misc**
* vararg parameter must be the last element in a method parameters list

**Task**
* Play with `protected` modifier and figure out how it works in inheritance
* Play with pass by value and pass by reference with primitives and objects
  * see how things change if you use return
* Create exercises for method overloading?
  * when valid
  * when invalid
  * when static and not
  * when array or varargs
  * when using types that are subtypes of other types....which one is invoked
