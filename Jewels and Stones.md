# LeetCode JavaScript Solutions



## Jewels and Stones



**Description:**

You're given strings ```J``` representing the types of stones that are jewels, and ```S``` representing the stones you have.  Each character in ```S``` is a type of stone you have.  You want to know how many of the stones you have are also jewels.

The letters in ```J``` are guaranteed distinct, and all characters in ```J``` and ```S``` are letters. Letters are case sensitive, so ```"a"``` is considered a different type of stone from ```"A"```.

Example 1:
```
Input: J = "aA", S = "aAAbbbb"
Output: 3
```

Example 2:

```
Input: J = "z", S = "ZZ"
Output: 0
```

Notes:

```S``` and ```J``` will consist of letters and have length at most 50.
The characters in ```J``` are distinct.

---


### Solution


```JavaScript

numJewelsInStones = (J, S) => {
    const jewels = new Set(J) // Creates a new Set object of jewels
    return S.split('') // splits stones into an array
    .reduce((acc, cur) => acc + jewels.has(cur), 0) // sums number of jewels (using reduce()) contained in stones (via .has method)
}

//Tests
numJewelsInStones("aA", "aAAbbbb") // => 3
numJewelsInStones("z", "ZZ") // => 0

```


---


[See on LeetCode.com](https://leetcode.com/problems/jewels-and-stones/)


