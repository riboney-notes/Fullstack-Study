# Book Of Proof

* [Link](https://www.people.vcu.edu/~rhammack/BookOfProof)

## Chapter 1: Sets

<details>
  <summary>What is a set?</summary>
  
  * Collection of things (called elements)
  * Ex: `{...,−4,−3,−2,−1,0,1,2,3,4,...}`
</details>

<details>
  <summary>When are sets equal?</summary>
  
  * They are equal if they contain exactly the same elements
  * Order of elements in sets do not affect equality
</details>

<details>
  <summary>
    If "{1, {2,3}, {2,4}}", then is it true that "2 ∉ E", "3 ∉ E", and "4 ∉ E"?
  </summary>

  * No
  * Set `E` only has 3 elements: `1, {2,3}, and {2,4}`
</details>

<details>
  <summary> 
     Assuming that "[1 1 1 0]" and "[0 1 1 0]" are matrices, and "M= {[1 1 1 0],[0 1 1 0]}", then is it true that "[0 1 1 1] ∉ M" and "[1 0 0 1] ∉ M"?
  </summary>

  * No
</details>

<details>
  <summary>What is the cardinality/ size of a set?</summary>

  * Number of elements a set has
</details>
    
<details>
  <summary>What is the cardinality of the set `{}`?</summary>

  * 0
  * Called empty set
  * denoted with symbol with a 0 that has a diagonal slash through it (can't be shown here)
</details>

<details>
  <summary>Is `{} == { {} }` true?</summary>

  * No, because `{}` contains nothing while `{{}}` contains one thing, an empty set
</details>

<details>
  <summary>What is the set-builder notation used for?</summary>

  * Used to describe sets that are too big complex to list between braces
  * Its another way to display sets
  * Ex: `E = {2n:n ∈ Z}`; E equals the set of all things of form `2n`, such that `n` is an element of Z (even numbers)
  * Syntax: `X = {expression:rule}`, where the elements of `X` are understood to be all values of `expression` that are specified by `rule`
</details>

<details>
  <summary>
    What does the expression `|X|` mean if `X` is number? What does it mean if `X` is a set?
  </summary>

  * Means absolute value if number
  * Means cardinality if set
</details>

<details>
  <summary>
    If `A = { {1,2}, {3,4,5,6}, {7} }` and `B = {X ∈ A: |X|<3}`, then what is `B`?
  </summary>

  * `B = { {1,2}, {7} }`
</details>

### 1.2 Cartesian Product

<details>
  <summary>
    What is an ordered pair?
  </summary>

  * list `(x,y)` of two "things" (can be anything..numbers, letters, or even ordered pairs) `x` and `y` enclosed in parentheses and separated by a comma
  * Ex: `(2,4)` is an ordered pair
</details>

<details>
  <summary>
    What is a Cartesian product?
  </summary>

  * product of two sets `A` and `B` that is a set denoted as `A x B` and defined as `A x B = {(a,b): a ∈ A, b ∈ B}`
  * Ex: Given `A = {k, l, m}` and `B = {q, r}`, `A x B = {(k,q), (k,r), (l,q), (l,r), (m,q), (m,r)}`
</details>

<details>
  <summary>
    Given `A` and `B` are finite sets, what is the cardinality of the set `A x B`?
  </summary>

  * `|A x B| = |A| * |B|`
  * Just multiply the size of A and B
</details>

<details>
  <summary>
    Given that `A = {}` and `B = {1,2}`, what is `A x B`?
  </summary>

  * It is `{}` (empty set)
</details>

<details>
  <summary>
    What is a subset?
  </summary>

  * Suppose `A` and `B` are sets. If every element of `A` is also an element of `B`, then we say `A` is a subset of `B` and this is denoted as `A ⊆ B`
  * If there is *at least* one element of `A` that is not an element of `B`, then `A` is not a subset of `B`
</details>

<details>
  <summary>
    Is `{}` ⊆ `{}`?
  </summary>

  * Yes
</details>

<details>
  <summary>
    Is empty set a subset of all sets? If so, why?
  </summary>

  * According to definition of subset, a set is not a subset if there is atleast one element not in the set...since `{}` is an empty set, that means that there is no elements in `{}` that is an element of any random set...there for `{} ⊆ AnySet`
</details>

<details>
  <summary>
    If a finite set has `n` elements, then how many subsets does it have?
  </summary>

  * It has `2^n` subsets
</details>
