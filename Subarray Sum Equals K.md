# LeetCode JavaScript Solutions



## Subarray Sum Equals K



**Description:**

Given an array of integers and an integer k, you need to find the total number of continuous subarrays whose sum equals to k.

Example 1:
```
Input:nums = [1,1,1], k = 2
Output: 2
```

Note:
- The length of the array is in range [1, 20,000].
- The range of numbers in the array is [-1000, 1000] and the range of the integer k is [-1e7, 1e7].

---

### Brute Force Solution
Complexity Analysis

- Time complexity : O(n^2) - Given an array as an input, the number of steps it takes to accomplish the task is the square of the array.

```JavaScript
// Tracks every subarray's sum within nums and checks if it's equal to K 
subArraySum = (nums, k) => {

  let counter = 0 

  for(i=0;i<nums.length;i++){
    let subArraySum = 0
    for (j=i;j<nums.length;j++){
      subArraySum += nums[j]
      if (subArraySum == k) {
        counter++
      }
    }
  }
  
  return counter
}

```


### Optimal Solution
Complexity Analysis

- Time complexity : O(n) - The entire array is traversed only once

```JavaScript
// Tracks the cumulative subarray sum by iterating through the array  
// only once and stores the value within a Map

// If the subarray sum has occured before 
// we increase the counter by it's total occurrances

subarraySum = (nums, k) => {
  const contArr = new Map() // declare map to store the cumulative subarray sums (as the keys),
  // and the numbers of those sums occurances (as the values)
  contArr.set(0,1) // sets first subarray sum (0) to have 1 occurance
  let counter = 0 // tracks the total number of continuous subarrays whose sum equals to K
  let subArraySum = 0 // sum of the subarray

  for(i=0;i<nums.length;i++){
    subArraySum += nums[i] // sets the sum equal to the current element in nums
    if(contArr.has(subArraySum-k)){ // if the map has the current subarray's sum in an earlier iteration
      counter += contArr.get(subArraySum-k) // we add that value's occurance to the counter
    }
    if(contArr.has(subArraySum)){ // if the map has the current subarray's sum
      contArr.set(subArraySum, contArr.get(subArraySum)+1) // we set the key to the sub array's sum
      // and add one to that key's value since the sum has occured again
    } else {
      contArr.set(subArraySum, 1) // sets the maps key to the sub array sum and adds one to keep track of it's occurance
    }
  }
  return counter // returns the total number of continious subarrays whose sum is equal to K
}

```


---


[See on LeetCode.com](https://leetcode.com/explore/featured/card/30-day-leetcoding-challenge/531/week-4/3307/)
