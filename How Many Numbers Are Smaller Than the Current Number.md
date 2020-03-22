# LeetCode JavaScript Solutions



## How Many Numbers Are Smaller Than the Current Number



**Description:**

Given the array nums, for each nums[i] find out how many numbers in the array are smaller than it. That is, for each nums[i] you have to count the number of valid j's such that j != i and nums[j] < nums[i].

Return the answer in an array.

 

Example 1:
```
Input: nums = [8,1,2,2,3]
Output: [4,0,1,1,3]
Explanation: 
For nums[0]=8 there exist four smaller numbers than it (1, 2, 2 and 3). 
For nums[1]=1 does not exist any smaller number than it.
For nums[2]=2 there exist one smaller number than it (1). 
For nums[3]=2 there exist one smaller number than it (1). 
For nums[4]=3 there exist three smaller numbers than it (1, 2 and 2).
```

Example 2:

```
Input: nums = [6,5,4,8]
Output: [2,1,0,3]
```

Example 3:
```
Input: nums = [7,7,7,7]
Output: [0,0,0,0]
```
Constraints:
```
2 <= nums.length <= 500
0 <= nums[i] <= 10
```

---


### Solution


```
smallerNumbersThanCurrent = (nums) => {
  let map = new Map();
  let sortedArr = nums.slice().sort((a,b) => a - b)

  for (i = 0; i < sortedArr.length; i++) {  
    if(!map.has(sortedArr[i])){
      map.set(sortedArr[i],i) 
    }
  }

  for (i = 0; i < sortedArr.length; i++) { 
      nums[i] = map.get(nums[i]); 
  }
      
  return nums;
}

```
---
### Testcase

nums = ```[8,1,2,2,3]```

Sort nums in ascending order:
```[1,2,2,3,8]```

Create map with counts:
```{1:0, 2:1, 3:3, 8:4}```

Return array with counts stored in map:
```[4,0,1,1,3]```


---


[See on LeetCode.com](https://leetcode.com/problems/how-many-numbers-are-smaller-than-the-current-number/)
