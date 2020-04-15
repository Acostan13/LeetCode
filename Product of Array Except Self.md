# LeetCode JavaScript Solutions



## Product of Array Except Self



**Description:**

Given an array ```nums``` of n integers where n > 1,  return an array ```output``` such that ```output[i]``` is equal to the product of all the elements of ```nums``` except ```nums[i]```.

Example:
```
Input:  [1,2,3,4]
Output: [24,12,8,6]
```

**Constraint:** It's guaranteed that the product of the elements of any prefix or suffix of the array (including the whole array) fits in a 32 bit integer.

**Note:** Please solve it without division and in O(n).

**Follow-up:** Could you solve it with constant space complexity? (The output array does not count as extra space for the purpose of space complexity analysis.)

---


### Solution
Complexity Analysis

- Time complexity : Linear Time - O(2n). The entire array is traversed twice.

- Space complexity: Constant Time - O(1). Given an input of size nums, it only takes a single step for the algorithm to accomplish the task.


```JavaScript
productExceptSelf = (nums) => {
  // Final answer array to be returned
  let products = []

  // leftProduct contains the product of all the elements to the left
  // Note: for the element at curInd '0', there are no elements to the left
  // so we start at index 1
  nums.reduce((leftProduct, curVal, curInd) => {  // reduce from left-to-right
    products[curInd] = leftProduct // updates products with left side product
    return leftProduct * curVal // returns current product with previously found product
  }, 1)

  // rightProduct contains the product of all the elements to the right
  // Note: for the element at curInd, there are no elements to the right
  // so we start at index 1
  nums.reduceRight((rightProduct, curVal, curInd) => { // reduce from right-to-left
    products[curInd] *= rightProduct // updates products with right side product
    return rightProduct * curVal // returns current product with previously found product
  }, 1)

  return products
}
```


---


[See on LeetCode.com](https://leetcode.com/explore/featured/card/30-day-leetcoding-challenge/530/week-3/3300)
