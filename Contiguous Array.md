# LeetCode JavaScript Solutions



## Contiguous Array



**Description:**

Given a binary array, find the maximum length of a contiguous subarray with equal number of ```0``` and ```1```.

Example 1:
```
Input: [0,1]
Output: 2
Explanation: [0, 1] is the longest contiguous subarray with equal number of 0 and 1.
```

Example 2:

```
Input: [0,1,0]
Output: 2
Explanation: [0, 1] (or [1, 0]) is a longest contiguous subarray with equal number of 0 and 1.
```

Note: The length of the given binary array will not exceed 50,000.

---


### Solution
Complexity Analysis

- Time complexity : O(n). The entire array is traversed only once

- Space complexity: O(n). Maximum size of the contiguous array map will be n, if all the elements are either ```1``` or ```0```.


```JavaScript
findMaxLength = (nums) => {
  const contArr = new Map() // declare map to store counter (as the key) and it's associated index (as the value)
  let maxConArr = 0 // max length of contiguous subarray
  let counter = 0 // counter for 1's and 0's in nums array
  contArr.set(0, -1) // set contArr key to 0 at index -1 since we haven't began looping through nums

  for(i=0; i<nums.length;i++){
    nums[i]===0 ? counter += -1 : counter += 1 // tracks balance of 1's and 0's
    if(contArr.has(counter)){ // when the same count values appear again
      maxConArr = Math.max(maxConArr, i - contArr.get(counter)) // we use the new index subtracting the old index to calculate the length of the subarray 
      // then compare it to our previous maximium contiguous subarray (using Math.max()) to find the new maximium contiguous subarray
    } else {
      contArr.set(counter, i) // sets the count value and its index if not previously seen
    }
  }

  return maxConArr
}

//Tests
findMaxLength([0,1,1,0,1,1,1,0]) // => 4
findMaxLength([0,1,0]) // => 2
findMaxLength([0,1]) // => 2
findMaxLength([]) // => 0
findMaxLength([0,0,0,0,0,0,0]) // => 0


```


---


[See on LeetCode.com](https://leetcode.com/explore/featured/card/30-day-leetcoding-challenge/529/week-2/3298/)
