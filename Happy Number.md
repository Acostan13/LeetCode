# LeetCode JavaScript Solutions



## Happy Number



**Description:**

Write an algorithm to determine if a number is "happy".

A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers.

Example 1:
```
Input: 19
Output: true
Explanation: 
12 + 92 = 82
82 + 22 = 68
62 + 82 = 100
12 + 02 + 02 = 1
```
---


### Solution


```JavaScript
isHappy = (n) => {
    let seen = new Set() // stores unique values
    while (n !== 1 && !seen.has(n)) { // if n is not equal to one AND not within seen
        seen.add(n) // adds n to seen
        n = reducedDigits(n) // calls reducedDigits function and set it equal to n
    }
    return n === 1 ? true : false // logic to determine whether number is happy or not
}

reducedDigits = (digits) => { // creates array of digits and reduces them
    return digits.toString().split('').reduce((sum, num) => { 
        return sum + Math.pow(num, 2) // adds the square of num to sum
    }, 0)
}

// Tests
isHappy(19) // => true
isHappy(14) // => false

// Happy Numbers in [1-99] => [1, 7, 10, 13, 19, 23, 28, 31, 32, 44, 49, 68, 70, 79, 82, 86, 91, 94, 97]
```


---


[See on LeetCode.com](https://leetcode.com/problems/happy-number/)










