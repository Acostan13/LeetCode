# LeetCode JavaScript Solutions



## Search in Rotated Sorted Array



**Description:**

Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.

(i.e., ```[0,1,2,4,5,6,7]``` might become ```[4,5,6,7,0,1,2]```).

You are given a target value to search. If found in the array return its index, otherwise return ```-1```.

You may assume no duplicate exists in the array.

Your algorithm's runtime complexity must be in the order of O(log n).

Example 1:
```
Input: nums = [4,5,6,7,0,1,2], target = 0
Output: 4
```

Example 2:

```
Input: nums = [4,5,6,7,0,1,2], target = 0
Output: 4
```

---

### Solution - Binary Search

Complexity Analysis

- Time complexity : O(log n) - Logarithmic Time: The number of steps it takes to find the target value are cut in half with each step

```JavaScript
const search = (nums, target) => {
  // Define Start and End Index
  let startIndex = 0
  let endIndex = nums.length - 1

  // Check to see if nums has a length or value
  if(nums.length === 0 || nums === null) return -1

  // Check to see if target is within nums array 
  if(!nums.includes(target)) return -1
  
  // While Start Index is less than or equal to End Index
  while(startIndex <= endIndex) {

    // Define Middle Index (This will change when comparing indices)
    let middleIndex = Math.floor((startIndex + endIndex) / 2)

    // Compare Middle Index with Target for match
    if(target === nums[middleIndex]) {
      return middleIndex
    }

    // When dividing the rotated array into two halves, one must ALWAYS be sorted
    // If one side is sorted, check if the target is in the boundary, otherwise it's on the other side.

    // Search left side
    // Check if the left side is sorted
    else if(nums[startIndex] <= nums[middleIndex]) {
      if(nums[startIndex] <= target && target <=nums[middleIndex]){
        // Decrease End Index by 1 to narrow search to the left side
        endIndex = middleIndex - 1
      } else {
        // Increase End Index by 1 to narrow search to the right side
        startIndex = middleIndex + 1
      }
    }

    // Search Right Side Of Array
    // Check if the right side is sorted
    else if(nums[startIndex] > nums[middleIndex]) {
      if(nums[middleIndex] <= target && target <= nums[endIndex]){
        // Increase Start Index by 1 to narrow search to the right side
        startIndex = middleIndex + 1
      } else {
        // Decrease End Index by 1 to narrow search to the left side
        endIndex = middleIndex - 1
      }
    }

  }
}
 
// Tests
search([4,5,6,7,8,1,2,3], 8) // => 4
search([4,5,6,7,0,1,2], 0) // => 4
search([4,5,6,7,0,1,2], 3) // => -1
search([], 5) // => -1
search([1], 1) // => 0
```


---


[See on LeetCode.com](https://leetcode.com/explore/featured/card/30-day-leetcoding-challenge/530/week-3/3304/)
