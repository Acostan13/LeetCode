# LeetCode JavaScript Solutions



## Perform String Shifts



**Description:**

You are given a string ```s``` containing lowercase English letters, and a matrix ```shift```, where ```shift[i] = [direction, amount]```:

- ```direction``` can be ```0``` (for left shift) or ```1``` (for right shift). 
- ```amount``` is the amount by which string ```s``` is to be shifted.
- A left shift by 1 means remove the first character of ```s``` and append it to the end.
- Similarly, a right shift by 1 means remove the last character of ```s``` and add it to the beginning.

Return the final string after all operations.

Example 1:
```
Input: s = "abc", shift = [[0,1],[1,2]]
Output: "cab"
Explanation: 
[0,1] means shift to left by 1. "abc" -> "bca"
[1,2] means shift to right by 2. "bca" -> "cab"
```

Example 2:

```
Input: s = "abcdefg", shift = [[1,1],[1,1],[0,2],[1,3]]
Output: "efgabcd"
Explanation:  
[1,1] means shift to right by 1. "abcdefg" -> "gabcdef"
[1,1] means shift to right by 1. "gabcdef" -> "fgabcde"
[0,2] means shift to left by 2. "fgabcde" -> "abcdefg"
[1,3] means shift to right by 3. "abcdefg" -> "efgabcd"
```

Note:

- ```1 <= s.length <= 100```
- ```s``` only contains lower case English letters.
- ```1 <= shift.length <= 100```
- ```shift[i].length == 2```
- ```0 <= shift[i][0] <= 1```
- ```0 <= shift[i][1] <= 100```
---


### Solution


```JavaScript
stringShift = (s, shift) => {
	let totalShift = 0 // tracks balance of left and right shifts
	
	// calculates amount of left and right shifts
	for(i=0; i<shift.length; i++) {
		shift[i][0] == 0 ? totalShift -= shift[i][1] : totalShift += shift[i][1]
	}
  
        totalShift %= s.length // removes unnecessary shifts
	if (totalShift < 0) { // if there are more left side shifts then right side shifts
		totalShift = s.length + totalShift // convert to a positive shift amount
	}
    
	// Perform the shifts
	let leftSide = s.substring(s.length - totalShift) // from right side of initial string
	let rightSide = s.substring(0, s.length - totalShift) // from left side of initial string

	return leftSide + rightSide
}
```

---


[See on LeetCode.com](https://leetcode.com/explore/featured/card/30-day-leetcoding-challenge/529/week-2/3299)
