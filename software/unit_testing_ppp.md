# Unit Testing Principles, Practices, and Patterns

## 1: The goal of unit testing

- When code is tightly coupled, its hard to test them separately
- Goal of unit testing
  - Enable sustainable growth of a project
  - Its hard to sustain the growth of a project without tests due to software entropy
- Software entropy
  - phenonmenon of quickly decreasing development speed
  - caused by changes made to the code base which can lead to complexity and disorganization
  - Ex: fixing bug causes more bugs, or changing code breaks code elsewhere
- Regression
  - aka bug
  - when a feature stops working as intended after a certain event (ie code modification)
- Cost components of testing activities
  - Refactoring the test in response to refactoring code base
  - Running tests for each code changes
  - Dealing with false alarms
  - Trying to understand tests
- Coverage metric
  - percentage that shows how much a source code a test suite executes 

*left off on 1.3 Using coverage metrics...*

