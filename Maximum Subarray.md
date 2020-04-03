# LeetCode JavaScript Solutions



## Maximum Subarray



**Description:**

Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

Example 1:
```
Input: [-2,1,-3,4,-1,2,1,-5,4],
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.
```

Follow up:
If you have figured out the O(n) solution, try coding another solution using the divide and conquer approach, which is more subtle.

---


### Brute force approach: O(n^3) solution => Cubic Algorithm


```Javascript
// For all pairs of integers, i ≤ j, check whether the sum of A[i..j] is greater than the maximum sum so far
maxSubArray = (nums) => {
  let max_so_far = 0
  let leftIndex = 0
  let rightIndex = nums.length - 1

  for (i = 0; i < nums.length; i++) {
      for (j = i; j < nums.length; j++) {
          maxSum = 0
           for (k = i; k <= j; k++) {
              maxSum += nums[k]
              if (max_so_far < maxSum) {
                  max_so_far = maxSum
              }
        }
      }
  }
    return max_so_far
}
```

### O(n^2) solution => Quadratic Algorithm


```Javascript
// Idea: The sum of A[i..j] can be efficiently calculated as (sum of A[i..j-1]) + A[j]
maxSubArray = (nums) => {
  let max_so_far = 0
  let leftIndex = 0
  let rightIndex = nums.length - 1
  
  for(i=0;i<nums.length;i++){
    maxSum = 0
    for(j=i;j<nums.length;j++){
      maxSum+=nums[j]
      if(max_so_far < maxSum){
        max_so_far = maxSum
      }
    }
  }
  return max_so_far
}
```

### 0(n) solution => Kadane's Algorithm

Explanation:
- Looks for all positive contiguous segments of the ```nums``` array
- ```global_max``` keeps track of maximum sum contiguous segment
- Each time we get a sum compare it (using ```Math.max()```) with ```local_max```
- Updates ```global_max``` if it is less than ```local_max```

```Javascript
maxSubArray = (nums) => {
  let local_max = 0
  let global_max = Number.NEGATIVE_INFINITY // largest negative infinity number

  for(i=0;i<nums.length;i++){
    local_max = Math.max(nums[i], nums[i] + local_max)
    if(local_max > global_max){
      global_max = local_max
    }
  }
  return global_max
}

// Kadane's Algorithm written optimally and concisely
maxSubArray = (nums) => {
  for (let i = 1; i < nums.length; i++) {
    nums[i] = Math.max(nums[i], nums[i] + nums[i - 1])
  }
  return Math.max(...nums)
}

//Tests
maxSubArray([-2, -1, -3, -4, -1, -2, -1, -5, -4]) // => 0
maxSubArray([]) // => 0
maxSubArray([2, 1, 3, 4, 1, 2, 1, 5, 4]) // => 23
maxSubArray([-2, 1, -3, 4, -1, 2, 1, -5, 4]) // => 6
```

---


[See on LeetCode.com](https://leetcode.com/problems/maximum-subarray/)
