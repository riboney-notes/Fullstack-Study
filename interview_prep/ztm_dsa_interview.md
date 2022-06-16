# Mastering the Coding Interview: Data Structures + Algorithms

_Link to [course](https://www.udemy.com/course/master-the-coding-interview-data-structures-algorithms)_

## 2 - Getting More Interviews

**Resume Cheat Sheet**

- [ ] Use a pre-designed resume template    
- [ ] Make the resume fit on 1 page   
- [ ] Include words from job description
  - Recruiter should know what job you are applying for from your resume
  - Include skills and objective relevant to the job posting
- [ ] Include company name you are applying to
  - can be placed in the objective statement
- [ ] Does your first item on your resume reflect what they are looking for?
  - should be something relevent to what they need instead of random job experience   
- [ ] Experience titles demonstrate value
  - Emphasize job position over company name in job experience section   
- [ ] Do you have an online link?  
- [ ] Remove the word “I”  
- [ ] No buzzwords describing how great you are  
- [ ] Are you using Action words?
  - What did you do and what were the results (in your job experience)   
- [ ] Measure everything in terms of impact, don’t just describe your responsibilities  
- [ ] Technical Knowledge/Skills should include what they are looking for. Only show years if it is impressive  
- [ ] Include only sections/items that are impressive: Experience, Projects, Education, Technical Skills  
- [ ] No typos or bad grammar 

**Resume Resources**

- _How to write effective resume_ - [stackoverflow blog](https://stackoverflow.blog/2020/11/25/how-to-write-an-effective-developer-resume-advice-from-a-hiring-manager/)
- _Sample resumes_ - [cakeresume](https://www.cakeresume.com/Engineering-resume-samples)
- _Resume Maker Tool_ - [resumemaker.online](https://www.resumemaker.online/)

**Experience**

- Don't hesitate to apply to jobs that sounds "difficult"
  - Usually job postings are made to sound difficult than it really
  - Working in a job with things you are not experienced with is a good opportunity to learn new things and improve yourself
-  What to do if you don't have experience
  - Github
    - Contribute to open source projects
  - Build a website
  - Have 1 or 2 big projects
    - Ex: Use projects in place of work experience

## 3 - Big O

**What is good code?**
- Two factors can determine "good code":
  - Readability
    - readable by others
    - maintainable 
  - Scalability
    - Time complexity: how speed of program increases as data input increases
    - Space complexity: how memory used by program increases as data input increases
    - usually there is a compromise between time and space (less time might mean more space, and vice-versa)

**Big O**
- the language used for describing how long algorithm takes to run
- can be used to compare different algorithm
  - running time alone is not a good enough metric to compare or evaluate algorithms since different hardware can mean different running times
- talking about the "Big O" or scalablity of an algorithm means to talk about how much running times increase as input data increases

**O(n)**
- as input increases, the number of operations increase linearly with respect to number of inputs
- linear time

**O(1)**
- no matter how much input increases, the number of operations is always the same
- if there are 100 operations, then runtime complexity will be O(100)
  - even then, big O would be O(1) since we only care about how runtime increases (which in this case with O(100), would be constant...so effectively, O(1)) 
- constant time

**O(NxN)**
- quadtratic time
- usually nested for loops are O(N^2) or O(a X b) if the nested loops handle different data inputs 

**O(N!)**
- the "!" is factorial
- this is where you add a loop for every element
- very expensive

**Rules for determining Big O**
- Worst Case
  - algorithms may have best scenarios where it completes execution very quickly depending on optimal data input
    - ex: searching for element in an array of size 1
  - however, when determining Big O, we only focus on the worst case scenarios and ignore all other scenarios
    - ex: search for an element that is at the end of the array   
- Remove Constants
  - even if there are 100 operations in an algorithm, for big O notation we ignore it and drop the constants and only focus on the variable input data and how it affects the number of operations 
- Different terms for inputs
  - if there are different data input sources, then they should be expressed in Big O notation with their own variables
  - Ex: O(a + b) for operations that are executed in order
  - Ex: O(a X b) for operations that are nested 
- Drop non dominants
  - when runtime complexity is a function with many terms, only keep the leading term with the highest degree 

**Space complexity causes**
- variables
- data structures
- function calls
- allocations

## 4 - How to Solve Problems

**What companies look for**
- Analytic skills
- Coding skills
- Tehcnical skills
- Communication skills

**DSA to know to solve most coding problems**
- Data structures
  - Arrays
  - Trees
  - Stacks
  - Tries
  - Queues
  - Graphs
  - Linked Lists
  - Hash Tables
- Algorithms
  - Sorting
  - Dynamic Programming
  - BFS + DFS (searching)
  - Recursion

**Whiteboard interview tips**
- Ask questions to clarify problem
  - input 
  - output
  - goal (time? space?)
  - contraints (how big the array will get, limitations, etc)
- Start with brute force approach
  - Explain the approach and why its bad/ not ideal 
  - this is so you have the chance to show critical thinking skills
- Verbally think out loud so they can see your thought process
  - can write these as comments in the code body before code is implemented 
- Consider edge cases and bring it up in your code
- Test your code
- Ask for feedback
