# LeetCode JavaScript Solutions



## Valid Parenthesis String



**Description:**

Given a string containing only three types of characters: '(', ')' and '*', write a function to check whether this string is valid. We define the validity of a string by these rules:

- Any left parenthesis ```'('``` must have a corresponding right parenthesis ```')'```.
- Any right parenthesis ```')'``` must have a corresponding left parenthesis ```'('```.
- Left parenthesis ```'('``` must go before the corresponding right parenthesis ```')'```.
- ```'*'``` could be treated as a single right parenthesis ```')'``` or a single left parenthesis ```'('``` or an empty string.
- An empty string is also valid.

Example 1:
```
Input: "()"
Output: True
```

Example 2:

```
Input: "(*)"
Output: True
```

Example 3:

```
Input: "(*))"
Output: True
```

Note: The string size will be in the range [1, 100].

---


### Greedy Solution

Complexity Analysis

- Time Complexity: O(N), where N is the length of the string. We iterate through the string once.

- Space Complexity: O(1), the space used by our ```lowerCount``` and ```upperCount``` counters. However, creating a new character array will take O(N) space.


```JavaScript
checkValidString = (s) => {
  
  let splitChars = s.split('') // array of chars
  let lowerCount = 0 // smallest and largest possible number of open left brackets 
  let upperCount = 0 // after processing the current character in the string

  for(i=0;i<splitChars.length;i++){
    // if we encounter a left parenthesis, then lowerCount++
    // else we could write a right right bracket, so lowerCount--
    lowerCount += splitChars[i] === '(' ? 1 : -1
    // if we encounter a left parenthesis, then upperCount++
    // else we must write a right right bracket, so upperCount--
    upperCount += splitChars[i] !== ')' ? 1 : -1
    // if we have no left brackets,  
    // then the current prefix can't be made valid no matter what our choices are
    if(upperCount < 0) break

    // check that we can have exactly 0 open left brackets
    lowerCount = Math.max(lowerCount, 0)
  }
  return lowerCount === 0
}

//Tests
checkValidString('(*))') // => true
checkValidString('(***)') // => true
checkValidString('(*)') // => true
checkValidString(')(*') // => false
checkValidString('*)') // => true
checkValidString('()') // => true
checkValidString(')(') // => false


```


---


[See on LeetCode.com](https://leetcode.com/explore/featured/card/30-day-leetcoding-challenge/530/week-3/3301/)
