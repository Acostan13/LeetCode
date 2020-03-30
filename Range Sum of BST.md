# LeetCode JavaScript Solutions



## Range Sum of BST



**Description:**

Given the ```root``` node of a binary search tree, return the sum of values of all nodes with value between ```L``` and ```R``` (inclusive).

The binary search tree is guaranteed to have unique values.

Example 1:
```
Input: root = [10,5,15,3,7,null,18], L = 7, R = 15
Output: 32
```

Example 2:

```
Input: root = [10,5,15,3,7,null,18], L = 7, R = 15
Output: 32
```

Note:

The number of nodes in the tree is at most ```10000```.
The final answer is guaranteed to be less than ```2^31```.

---


### Solution


```JavaScript
/**
 * @param {TreeNode} root
 * @param {number} L
 * @param {number} R
 * @return {number}
 */
rangeSumBST = (root, L, R) => {

  // check if value is in the given range
  const isInBetween = val => val >= L && val <= R

  // sum the value if it's in the range
  const add = (val, sum) => isInBetween(val) ? sum += val : sum

	// traverse through the nodes and sum the values in range
  const preorder =(root, sum) => {
        if (!root) return sum
        return add(root.val, sum) + preorder(root.left, sum) + preorder(root.right, sum)
    } 
    return preorder(root, 0)
}

//Tests
rangeSumBST([10,5,15,3,7,null,18], L = 7, R = 15) // => 32
rangeSumBST([10,5,15,3,7,13,18,1,null,6], L = 6, R = 10) // => 23

```


---


[See on LeetCode.com](https://leetcode.com/problems/range-sum-of-bst/)
