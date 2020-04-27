# LeetCode JavaScript Solutions



## Maximal Square



**Description:**

Given a 2D binary matrix filled with 0's and 1's, find the largest square containing only 1's and return its area.

**Example 1:**
```
Input: 

1 0 1 0 0
1 0 1 1 1
1 1 1 1 1
1 0 0 1 0

Output: 4
```

---


### Solution
Complexity Analysis

- Time complexity : O(m*n). The entire 2D array is traversed once.


```JavaScript
maximalSquare = (matrix) => {
    if (!matrix.length) return 0
    
    // Initialized 2d Matrix from matrix input
    let dp = new Array(matrix.length+1).fill(0).map(()=>new Array(matrix[0].length+1).fill(0))
    let max = 0
    
    for (r=1;r<dp.length;r++) { 
        for (c=1;c<dp[0].length;c++) {
        
            // if the matrix indice contains a 1
            if (matrix[r-1][c-1]!=0) {
            
                // find the min value from the left, above, and left-diagonal position 
                // relative to the current indice, then add 1 to it
                dp[r][c] = Math.min(dp[r][c-1], dp[r-1][c], dp[r-1][c-1])+1
                
                // compares current with previous maximal square
                max = Math.max(dp[r][c], max)
            }
        }
    }
    return max**2
}

```


---


[See on LeetCode.com](https://leetcode.com/explore/featured/card/30-day-leetcoding-challenge/531/week-4/3312/)
