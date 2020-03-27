# LeetCode JavaScript Solutions



## Subtract the Product and Sum of Digits of an Integer



**Description:**

Given an integer number ```n```, return the difference between the product of its digits and the sum of its digits.

Example 1:
```
Input: n = 234
Output: 15 
Explanation: 
Product of digits = 2 * 3 * 4 = 24 
Sum of digits = 2 + 3 + 4 = 9 
Result = 24 - 9 = 15
```

Example 2:

```
Input: n = 4421
Output: 21
Explanation: 
Product of digits = 4 * 4 * 2 * 1 = 32 
Sum of digits = 4 + 4 + 2 + 1 = 11 
Result = 32 - 11 = 21
```

Constraints:
```
1 <= n <= 10^5
```
---


### Solution


```JavaScript
subtractProductAndSum = (n) => {
    let digits = n.toString().split("").map(Number); // creates array of digits
   
    /* This could also be used to find digits:
    const digits = Array.from(String(n), Number)
    */
    
    let sum = digits.reduce((acc, cur)=>{
      return acc + cur
    })
    
    let product = digits.reduce((acc, cur)=>{
      return acc * cur
    })
    
    return product - sum
}



//Tests
subtractProductAndSum(234) // => 15
subtractProductAndSum(4421) // => 21

```


---


[See on LeetCode.com](https://leetcode.com/problems/subtract-the-product-and-sum-of-digits-of-an-integer/)
