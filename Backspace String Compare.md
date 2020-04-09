# LeetCode JavaScript Solutions



## Backspace String Compare



**Description:**

Given two strings ```S``` and ```T```, return if they are equal when both are typed into empty text editors. ```#``` means a backspace character.

Example 1:
```
Input: S = "ab#c", T = "ad#c"
Output: true
Explanation: Both S and T become "ac".
```

Example 2:

```
Input: S = "ab##", T = "c#d#"
Output: true
Explanation: Both S and T become "".
```

Example 3:

```
Input: S = "a##c", T = "#a#c"
Output: true
Explanation: Both S and T become "c".
```

Example 4:

```
Input: S = "a#c", T = "b"
Output: false
Explanation: S becomes "c" while T becomes "b".
```

Note:

- ```1 <= S.length <= 200```
- ```1 <= T.length <= 200```
- ```S``` and ```T``` only contain lowercase letters and ```'#'``` characters.
---


### Solution


```JavaScript
backspaceCompare = (S, T) => {
  const backspacedString = str => {
  const stack = []
    for (const char of str) { // iterates through each string character
      if (char === '#') {
        stack.pop() // removes last element of stack
      } else {
        stack.push(char) // adds char elements to stack
      }
    }
    return stack.join('') // concatenates all elements of stack into a string
  }
  return backspacedString(S) === backspacedString(T) // returns true if S and T are equal
} 

```

---


[See on LeetCode.com](https://leetcode.com/explore/featured/card/30-day-leetcoding-challenge/529/week-2/3291/)
