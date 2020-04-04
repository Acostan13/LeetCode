# LeetCode JavaScript Solutions



## Move Zeroes



**Description:**

Given an array ```nums```, write a function to move all ```0```'s to the end of it while maintaining the relative order of the non-zero elements.

Example:
```
Input: [0,1,0,3,12]
Output: [1,3,12,0,0]
```

Notes:
- You must do this in-place without making a copy of the array.
- Minimize the total number of operations.

---


### Initial solution
- Iterates through array backwards to avoid undefined when splicing

```Javascript
moveZeroes = (nums) => {
  for(i = nums.length - 1; i >= 0; i--){
    if (nums[i]=== 0) {
      nums.splice(i,1)
      nums.push(0)
    }
  }
  return nums
}
```

### Optimized solution
- Space Complexity : O(1)
- Time Complexity : O(n)


```Javascript
moveZeroes = (nums) => {
  let index = 0

  for(i=0;i<nums.length;i++){
    if(nums[i] !== 0){ // If the current element is not 0, then we need to
      nums[index++] = nums[i] // append it just in front of last non 0 element we found
    }
  }

/* After we have finished processing new elements,
all the non-zero elements are already at beginning of array.
We just need to fill remaining array with 0's. */
  for(i=index;i<nums.length;i++){
    nums[i] = 0
  }
  return nums
}
```

---


[See on LeetCode.com](https://leetcode.com/problems/move-zeroes/)
