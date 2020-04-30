# LeetCode JavaScript Solutions



## Check If a String Is a Valid Sequence from Root to Leaves Path in a Binary Tree



**Description:**

Given a binary tree where each path going from the root to any leaf form a valid sequence, check if a given string is a valid sequence in such binary tree. 

We get the given string from the concatenation of an array of integers ```arr``` and the concatenation of all values of the nodes along a path results in a sequence in the given binary tree.

**Example 1:**

```
Input: root = [0,1,0,0,1,0,null,null,1,0,0], arr = [0,1,0,1]
Output: true
Explanation: 
The path 0 -> 1 -> 0 -> 1 is a valid sequence. 
Other valid sequences are: 
0 -> 1 -> 1 -> 0 
0 -> 0 -> 0
```

**Example 2:**

```
Input: root = [0,1,0,0,1,0,null,null,1,0,0], arr = [0,0,1]
Output: false 
Explanation: The path 0 -> 0 -> 1 does not exist, therefore it is not even a sequence.
```

**Example 3:**

```
Input: root = [0,1,0,0,1,0,null,null,1,0,0], arr = [0,1,1]
Output: false
Explanation: The path 0 -> 1 -> 1 is a sequence, but it is not a valid sequence.
```

**Copnstraints**
- ```1 <= arr.length <= 5000```
- ```0 <= arr[i] <= 9```
- Each node's value is between [0 - 9].


---


### Solution


```JavaScript
isValidSequence = (root, arr) => {
    return valid(root, arr, 0)    
}


valid = (root, arr, pos) => {
    // if our position is at the end of the current subtree or the input arr
    // then the current sequence is NOT valid so return false
    if(!root || pos >= arr.length) return false
    
    
    // if current node is a leaf, 
    // check if the end of arr is reached, 
    // if it is a valid sequence then return true
    if(!root.left && !root.right) {
        if(pos === arr.length - 1 && arr[pos] === root.val){
            return true
        } else {
            return false
        }
    }
    
    
    // increase the position by 1 and recurse to the children
    // if both left and right paths are not valid, return false
    if(arr[pos] === root.val) {
        ++pos
        return valid(root.left, arr, pos) || valid(root.right, arr, pos)
    } else {
        return false
    }
} 

```


---


[See on LeetCode.com](https://leetcode.com/explore/featured/card/30-day-leetcoding-challenge/532/week-5/3315)
