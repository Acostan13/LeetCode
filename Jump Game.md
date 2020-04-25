# LeetCode JavaScript Solutions



## Jump Game



**Description:**

Given an array of non-negative integers, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Determine if you are able to reach the last index.

**Example 1:**
```
Input: [2,3,1,1,4]
Output: true
Explanation: Jump 1 step from index 0 to 1, then 3 steps to the last index.
```

**Example 2:**

```
Input: [3,2,1,0,4]
Output: false
Explanation: You will always arrive at index 3 no matter what. Its maximum
             jump length is 0, which makes it impossible to reach the last index.
```

---


### Solution

Complexity Analysis

- Time complexity : O(n) - We are doing a single pass through the nums array, hence n steps, where n is the length of array nums.


- Space complexity: O(1) - We are not using any extra memory.


```JavaScript
// Greedy algorithm => an algorithm that makes the optimal choice at each step going forward
canJump = (nums) => {

   // keep a record of the maximum possible index
    let maxIndex = 0

    for(i=0;i<nums.length;i++){
    
        // if an index is impossible, return false
        if(i > maxIndex) {return false}

        // keep updating maximum possible index to record how far you can jump so far
        maxIndex = Math.max(nums[i] + i, maxIndex)
    }
    return true
}

```


---


[See on LeetCode.com](https://leetcode.com/explore/featured/card/30-day-leetcoding-challenge/528/week-1/3287/)
