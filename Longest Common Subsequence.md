# LeetCode JavaScript Solutions



## Longest Common Subsequence




**Description:**

Given two strings ```text1``` and ```text2```, return the length of their longest common subsequence.

A subsequence of a string is a new string generated from the original string with some characters(can be none) deleted without changing the relative order of the remaining characters. (eg, "ace" is a subsequence of "abcde" while "aec" is not). A common subsequence of two strings is a subsequence that is common to both strings.

If there is no common subsequence, return 0.

**Example 1:**
```
Input: text1 = "abcde", text2 = "ace" 
Output: 3  
Explanation: The longest common subsequence is "ace" and its length is 3.
```

**Example 2:**

```
Input: text1 = "abc", text2 = "abc"
Output: 3
Explanation: The longest common subsequence is "abc" and its length is 3.
```

**Example 3:**
```
Input: text1 = "abc", text2 = "def"
Output: 0
Explanation: There is no such common subsequence, so the result is 0.
```

 

**Constraints:**

- ```1 <= text1.length <= 1000```
- ```1 <= text2.length <= 1000```
- The input strings consist of lowercase English characters only.

---


### Solution
Complexity Analysis

- Time complexity : O(m*n)

- Space complexity: O(m*n)


```JavaScript
longestCommonSubsequence = (text1, text2) => {
  // Initialized 2d Matrix from text inputs
  const dp = Array(text1.length + 1)
    .fill(0)
    .map(() => Array(text2.length + 1).fill(0))


  let maxCommonSubsequence = 0
  
  for(i = 1; i <= text1.length; i++) {
    for(j = 1; j <= text2.length; j++) {
      // if the characters from both texts match
      if(text1[i - 1] === text2[j - 1]) {
        // add 1 to the current longest common subsequence at index [i][j]
        dp[i][j] = 1 + dp[i - 1][j - 1]
      } else {
        // compare it the the previous longest common subsequence to see which is larger
        dp[i][j] = Math.max(dp[i - 1][j], dp[i][j - 1])
      }
      // compares current with previous longest common subsequence
      maxCommonSubsequence = Math.max(maxCommonSubsequence, dp[i][j])
    }
  }
  return maxCommonSubsequence
}

```


---


[See on LeetCode.com](https://leetcode.com/explore/featured/card/30-day-leetcoding-challenge/531/week-4/3311/)
