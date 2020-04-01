# LeetCode JavaScript Solutions



## Single Number



**Description:**

Given a non-empty array of integers, every element appears twice except for one. Find that single one.

Note: Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?


Example 1:
```
Input: [2,2,1]
Output: 1
```
Example 2:
```
Input: [4,1,2,1,2]
Output: 4
```

---


### Solution


```JavaScript
// Initial solution creating a counts object and finding the key with value of 1
singleNumber = (nums) => {
  let counts = {}
  
  nums.forEach(function(x) { counts[x] = (counts[x] || 0)+1;
  })
  
  for (var key in counts){
   if(counts[key] === 1) return key
  }
}

// Optimized solution using reduce and bitwise XOR operation
// ^ operator => whenever a new value is found , (prev) will include it, else remove the value from (prev);
singleNumber = (nums) => {
 return nums.reduce((prev, curr) => prev ^ curr, 0);
}

// Tests
singleNumber([2,2,1]) // => 1
singleNumber([4,1,2,1,2]) // => 4

```


---


[See on LeetCode.com](https://leetcode.com/problems/single-number/)
