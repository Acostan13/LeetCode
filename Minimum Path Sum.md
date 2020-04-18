# LeetCode JavaScript Solutions



## Minimum Path Sum



**Description:**

Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right which minimizes the sum of all numbers along its path.

Note: You can only move either down or right at any point in time.

Example 1:
```
Input:
[
  [1,3,1],
  [1,5,1],
  [4,2,1]
]
Output: 7
Explanation: Because the path 1→3→1→1→1 minimizes the sum.
```

---


### Solution
Complexity Analysis

- Time complexity : O(mn). The entire 2d array is traversed only once

- Space complexity: O(1). Given an input of size grid, it only takes a single step for the algorithm to accomplish the task


```JavaScript
minPathSum = (grid) => {
  // Get the two dimensions of the grid
  const n = grid.length
  const m = grid[0].length
    
  // Calculate the distance travelled within the first column
  // This is because each value depends on the one above it
  // And the one to the left of it. However there is nothing
  // left of the first column so we can calculate it by adding
  // the current value to the value above it
  for(row=1; row<n; row++) {
     grid[row][0] += grid[row-1][0]
  }
    
  // The same goes for the first row. There is nothing above the 
  // first row. So we just calculate the distance by what is to the left
  // of it
  for(col=1; col<m; col++) {
    grid[0][col] += grid[0][col-1]
  }
  // Start one row and one column in because we've precomputed
  // those above
  for(row=1; row<n; row++) {
    for(col=1; col<m; col++) {
      // The distance to the grid at [row][col] is equal to itself plus the minimum
      // of the two grid spaces (one above, one to the left)
      grid[row][col] += Math.min(grid[row-1][col], grid[row][col-1])
    }
  }
  // Return the minimum sum path to the bottom right corner
  return grid[n-1][m-1]
}


```


---


[See on LeetCode.com](https://leetcode.com/explore/featured/card/30-day-leetcoding-challenge/530/week-3/3303)
