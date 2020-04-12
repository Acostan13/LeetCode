# LeetCode JavaScript Solutions



## Diameter of Binary Tree


**Description:**

Given a binary tree, you need to compute the length of the diameter of the tree. The diameter of a binary tree is the length of the longest path between any two nodes in a tree. This path may or may not pass through the root.

Example:

Given a binary tree
```
          1
         / \
        2   3
       / \     
      4   5  
```
Return ```3```, which is the length of the path ```[4,2,1,3]``` or ```[5,2,1,3]```.

Note: The length of path between two nodes is represented by the number of edges between them.

---


### Solution


```JavaScript
diameterOfBinaryTree = (root) => {
    let maxDistance = 0

    const depth = root => {
        if(root==null) return 0
        
        // get the length of left and right sub-trees
        let left = depth(root.left) 
        let right = depth(root.right)
        
        // set maxDistance to previous or current root depth
        maxDistance = Math.max(maxDistance, left + right)
        
        // return diameter
        return Math.max(left, right) + 1
    }
    
    depth(root)
    
    return maxDistance
} 
```

---


[See on LeetCode.com](https://leetcode.com/explore/featured/card/30-day-leetcoding-challenge/529/week-2/3293/)
