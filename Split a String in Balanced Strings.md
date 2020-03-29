# LeetCode JavaScript Solutions



## Split a String in Balanced Strings



**Description:**

Balanced strings are those who have equal quantity of 'L' and 'R' characters.

Given a balanced string ```s``` split it in the maximum amount of balanced strings.

Return the maximum amount of splitted balanced strings.

 

Example 1:
```
Input: s = "RLRRLLRLRL"
Output: 4
Explanation: s can be split into "RL", "RRLL", "RL", "RL", each substring contains same number of 'L' and 'R'.
```
Example 2:
```
Input: s = "RLLLLRRRLR"
Output: 3
Explanation: s can be split into "RL", "LLLRRR", "LR", each substring contains same number of 'L' and 'R'.
```
Example 3:
```
Input: s = "LLLLRRRR"
Output: 1
Explanation: s can be split into "LLLLRRRR".
```
Example 4:
```
Input: s = "RLRRRLLRLL"
Output: 2
Explanation: s can be split into "RL", "RRRLLRLL", since each substring contains an equal number of 'L' and 'R'.
```

Constraints:
```
1 <= s.length <= 1000
s[i] = 'L' or 'R'
```

---


### Solutions

```JavaScript
// Initial solution
balancedStringSplit = (s) => {
  let arr = []
  let rCount = 0 // 'R' count
  let lCount = 0 // 'L' count
  let balStringCount = 0 // Balanced string count
    
  for(i=0;i<s.length;i++){
    arr.push(s.charAt(i))
    if (s.charAt(i) === 'R'){
      rCount++
    } else {
      lCount++
    }
    if (rCount === lCount){ // if there are equal amounts of L's and R's in the array
      balStringCount++ // increases balanced string count by 1
      arr = [] // clears array
    }
  }
  return balStringCount
}

// Optimized Solution with Time: O(n) & Space: O(1)
balancedStringSplit = (s) => {
    let balance = 0
    let count = 0
    
    for (let i = 0; i < s.length; i++) {
        if (s[i] === 'L') {
            balance -= 1
        } else {
            balance += 1
        }
        
        if (balance === 0) {
            count++
        }
    }
    
    return count
}

// Tests
balancedStringSplit("RLRRLLRLRL")
balancedStringSplit("RLLLLRRRLR")
balancedStringSplit("LLLLRRRR")
balancedStringSplit("RLRRRLLRLL")
```
---


[See on LeetCode.com](https://leetcode.com/problems/split-a-string-in-balanced-strings/)
