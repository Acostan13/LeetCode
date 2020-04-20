# LeetCode JavaScript Solutions



## Construct Binary Search Tree from Preorder Traversal



**Description:**

Return the root node of a binary search tree that matches the given ```preorder``` traversal.

(Recall that a binary search tree is a binary tree where for every node, any descendant of ```node.left``` has a value ```<``` ```node.val```, and any descendant of ```node.right``` has a value ```>``` ```node.val```.  Also recall that a preorder traversal displays the value of the ```node``` first, then traverses ```node.left```, then traverses ```node.right```.)

Example:
```
Input: [8,5,1,7,10,12]
Output: [8,5,10,1,7,null,12]
```

Note: The length of the given binary array will not exceed 50,000.

---


### Solution
Complexity Analysis

- Time complexity : O(n). The entire array is traversed only once

```JavaScript
bstFromPreorder = (preorder) => {
  if (!preorder.length) return null

  // Set range for the root node 
  // This means that the root node and any of its children can have keys
  // ranging between root and rest 
  const [root, ...rest] = preorder
  
  // Construct the root node of bst which is the first key in the preorder sequence
  const rootNode = new TreeNode(root)

  // Recursion for the left sub-tree with keys in the preorder sequence
  // that appears before the n'th index
  rootNode.left = bstFromPreorder(rest.filter(n => n < root))

  // Recursion for the right sub-tree with keys in the preorder sequence
  // that appears after the n'th index
  rootNode.right = bstFromPreorder(rest.filter(n => n > root))
    
  return rootNode
}

```


---


[See on LeetCode.com](https://leetcode.com/explore/featured/card/30-day-leetcoding-challenge/530/week-3/3305/)
