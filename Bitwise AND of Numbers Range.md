# LeetCode JavaScript Solutions



## Bitwise AND of Numbers Range



**Description:**

Given a range [m, n] where 0 <= m <= n <= 2147483647, return the bitwise AND of all numbers in this range, inclusive.

Example 1:
```
Input: [5,7]
Output: 4
```

Example 2:
```
Input: [0,1]
Output: 0
```

---

### Initial Solution
Traverse all numbers from x to y and do bit-wise and of all numbers in range:
1) Find position of Most Significant Bit (MSB) in both numbers.
2) If positions of MSB are different, then result is 0.
3) If positions are same. Let positions be msb_p:
  - a) We add 2msb_p to result.
  - b) We subtract 2msb_p from m and n,
  - c) Repeat steps 1, 2 and 3 for new values of m and n. 


```JavaScript
// Find position of MSB in n. For example  
// if n = 17, then position of MSB is 4.  
// If n = 7, value of MSB is 3  
msbPos = (i) => {
  let msb_p = -1
  while(i>0){
    i = i >> 1
    msb_p++
  }
  return msb_p
}

// Function to find Bit-wise & of all  
// numbers from m to n.
rangeBitwiseAnd = (m,n) => {
  let result = 0 // Initialize result  

  while(m > 0 && n > 0){
    // Find positions of MSB in m and n  
    let msb_p1 = msbPos(m)
    let msb_p2 = msbPos(n)

    // If positions are not same, return  
    if(msb_p1 != msb_p2){
      break
    }

    // Add 2^msb_p1 to result  
    let msb_val = (1 << msb_p1)
    result += msb_val

    // subtract 2^msb_p1 from m and n. 
    m -= msb_val
    n -= msb_val
  }
  return result
}
```


### Optimized Solution
1) Flip the LSB of n.
2) And check if the new number is in range(m <= number <= n) or not:
  - a) if the number is greater than 'n' flip lsb
  - b) if it is not then that's the answer

```JavaScript
rangeBitwiseAnd = (m,n) => {
  while(m < n){
    // -n is the 2's complement of n when we do bitwise or with n  
    // we get LSB and we subtract that from n 
    n-=(n & -n)
  }
  return n
}

```


---


[See on LeetCode.com](https://leetcode.com/explore/featured/card/30-day-leetcoding-challenge/531/week-4/3307/)
