# LeetCode JavaScript Solutions



## Maximum 69 Number



**Description:**

Given a positive integer num consisting only of digits 6 and 9.

Return the maximum number you can get by changing at most one digit (6 becomes 9, and 9 becomes 6).

Example 1:
```
Input: num = 9669
Output: 9969
Explanation: 
Changing the first digit results in 6669.
Changing the second digit results in 9969.
Changing the third digit results in 9699.
Changing the fourth digit results in 9666. 
The maximum number is 9969.
```

Example 2:

```
Input: num = 9996
Output: 9999
Explanation: Changing the last digit 6 to 9 results in the maximum number.
```

Example 3:
```
Input: num = 9999
Output: 9999
Explanation: It is better not to apply any change.
```
Constraints:
```
1 <= num <= 10^4
num's digits are 6 or 9.
```

---


### Solution


```JavaScript
maximum69Number = (num) => {
  let StringNum = String(num)
    for(i=0;i<StringNum.length;i++) {
        if(StringNum.charAt(i) === "6") {
            return Number(StringNum.replace("6","9"))
        }
    }
    return num
};

//Tests
maximum69Number("9669")
maximum69Number("66666")
maximum69Number("96969")
maximum69Number("99999")
maximum69Number("66696")

```


---


[See on LeetCode.com](https://leetcode.com/problems/maximum-69-number/)
