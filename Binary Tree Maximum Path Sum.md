# LeetCode JavaScript Solutions



## Binary Tree Maximum Path Sum



**Description:**

Given a non-empty binary tree, find the maximum path sum.

For this problem, a path is defined as any sequence of nodes from some starting node to any node in the tree along the parent-child connections. The path must contain at least one node and does not need to go through the root.

**Example 1:**
```
Input: [1,2,3]

       1
      / \
     2   3

Output: 6
```

**Example 2:**

```
Input: [-10,9,20,null,null,15,7]

   -10
   / \
  9  20
    /  \
   15   7

Output: 42
```

---


### Solution


```JavaScript
maxPathSum = (root) => {
  // Initialize to a very small number to handle a path of negative values
  let max_value = -Infinity
  
  maxSum = (node) => {
    if (!node) return 0 // termination condition
    
    let leftBranch = maxSum(node.left) // find the left leaf from the current node
    let rightBranch = maxSum(node.right) // find the right leaf from the current node

    // Sum the current path: left -> node -> right (leaf to leaf)
    let currentPath = leftBranch + node.val + rightBranch  
    
    // if the current path is greater than the previous value of `max_value`, 
    // update `max_value` to the current path sum
    max_value = Math.max(max_value, currentPath) 

    // finds the max value of the left path, right path, 
    // or zero if the left and right path are negative
    return Math.max(0, node.val + leftBranch, node.val + rightBranch)
  }

  // Call our recursive fn to start searching the binary tree
  maxSum(root) 
  
  // Once we have finished all of our recursive calls, 
  // `max_value` contains our maximum path sum
  return max_value 
}

```


---


[See on LeetCode.com](https://leetcode.com/explore/featured/card/30-day-leetcoding-challenge/532/week-5/3314/)
