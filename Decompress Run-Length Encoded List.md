# LeetCode JavaScript Solutions



## Decompress Run-Length Encoded List



**Description:**

We are given a list ```nums``` of integers representing a list compressed with run-length encoding.

Consider each adjacent pair of elements ```[freq, val] = [nums[2*i], nums[2*i+1]]``` (with ```i >= 0```).  For each such pair, there are ```freq``` elements with value ```val``` concatenated in a sublist. Concatenate all the sublists from left to right to generate the decompressed list.

Return the decompressed list.

Example 1:
```
Input: nums = [1,2,3,4]
Output: [2,4,4,4]
Explanation: The first pair [1,2] means we have freq = 1 and val = 2 so we generate the array [2].
The second pair [3,4] means we have freq = 3 and val = 4 so we generate [4,4,4].
At the end the concatenation [2] + [4,4,4] is [2,4,4,4].
```

Example 2:

```
Input: nums = [1,1,2,3]
Output: [1,3,3]
```

Constraints:
```
2 <= nums.length <= 100
nums.length % 2 == 0
1 <= nums[i] <= 100
```
---


### Solutions


```JavaScript
// Simple solution
decompressRLElist = (nums) => {
    let result = []; // declare new array
        
    for (let i = 0; i < nums.length; i += 2) { // iterate through every other nums array element
        const [freq, val] = [nums[i], nums[i+1]]; // declare freq/value according to pair of elements logic
        
        for (let j = 0; j < freq; j++) { // pushes every 'value' a 'freq' amount of times into result array
            result.push(val);
        }
    }
    return result;
}

// Optimized solution
decompressRLElist = (nums) => {
  const result = []; //declare new array
  
  for (let i = 1; i < nums.length; i += 2) { // loop through every other nums array element
    result.push(...new Array(nums[i - 1]).fill(nums[i])); // pushes the new array value's into the result array and fills it with the frequency
  }
  return result;
}

//Tests
decompressRLElist([1,2,3,4]) // => [2,4,4,4]
decompressRLElist([1,1,2,3]) // => [1,3,3]

```


---


[See on LeetCode.com](https://leetcode.com/problems/decompress-run-length-encoded-list/)







