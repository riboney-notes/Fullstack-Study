# Leetcode patterns

## Sliding window

<details><summary>680. Valid Palindrome II</summary>
  
  - Link to [problem](https://leetcode.com/problems/valid-palindrome-ii/)
  - Problem: 
    - Given a string `s`, return true if the `s` can be palindrome after deleting at most one character from it.
  - Example 1:
    - Input: `s = "aba"`
    - Output: `true`
  - Example 2: 
    - Input: `s = "abca"`
    - Output: `false`
  - Constraints
    - `1 <= s.length <= 105`
    - `s` consists of lowercase English letters.
  - Initial thoughts
    - No idea how to approach this directly! 
    - I'm thinking first we have to create a function that determines whether a string is a palindrome
      - This function would have to take a string as an input, reverse the string, and compare the reversed string with the original string; output would be a boolean
    - Next, the problem is figuring out which character would need to be eliminated to find out if its a palindrome if one character is deleted
      - Not sure how to go about doing this
  - Solution:
  
    ![image](https://user-images.githubusercontent.com/14286113/161384044-5481b79a-e185-4afb-a6af-1aa772ed3c97.png)
    ![image](https://user-images.githubusercontent.com/14286113/161384098-f344c680-06b2-47e5-b888-15c5e1a66c34.png)
    ![image](https://user-images.githubusercontent.com/14286113/161384106-c19266bc-a52c-4137-8e1d-64b54ca24656.png)

</details>
  
