# LeetCode JavaScript Solutions



## Group Anagrams



**Description:**

Given an array of strings, group anagrams together.

Example:
```
Input: ["eat", "tea", "tan", "ate", "nat", "bat"],
Output:
[
  ["ate","eat","tea"],
  ["nat","tan"],
  ["bat"]
]
```
Note:

- All inputs will be in lowercase.
- The order of your output does not matter.
---


### Solution


```JavaScript
groupAnagrams = (strs) => {
    /* Map with each key as the sorted string and 
    each value as the list of strings from intitial input */
    const anagrams = new Map()
    
    for (let i = 0; i < strs.length; i++) {
        const wordSorted = strs[i].split('').sort().join('') // sorts the words
        if (anagrams.has(wordSorted)) { // If the sorted word matches any existing sorted word
            anagrams.get(wordSorted).push(strs[i]) // add it to the anagrams values
        } else { // If our sorted word doesn't match anything
            anagrams.set(wordSorted, [strs[i]]) // add a new entry to the map
        }
    }
    return [...anagrams.values()] // returns a new array of values from anagram map
}
```

---


[See on LeetCode.com](https://leetcode.com/problems/group-anagrams/)
