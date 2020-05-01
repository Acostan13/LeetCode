# LeetCode JavaScript Solutions



## Convert Binary Number in a Linked List to Integer



**Description:**

Given ```head``` which is a reference node to a singly-linked list. The value of each node in the linked list is either 0 or 1. The linked list holds the binary representation of a number.

Return the decimal value of the number in the linked list.

**Example 1:**
```
Input: head = [1,0,1]
Output: 5
Explanation: (101) in base 2 = (5) in base 10
```
**Example 2:**
```
Input: head = [0]
Output: 0
```
**Example 3:**
```
Input: head = [1]
Output: 1
```
**Example 4:**
```
Input: head = [1,0,0,1,0,0,1,1,1,0,0,0,0,0,0]
Output: 18880
```

---


### Solution
Complexity Analysis

- Time complexity : O(n). The entire linked list is traversed once.


```JavaScript
let getDecimalValue = (head) => {
    let result = 0
    
    // head is not null
    while(head){
        
        // Changes log base of head value to binary
        // Sums binary value to the result variable
        result = result*2 + head.val 

        // moves to next value in linked list
        head = head.next
    }
    
    return result
}

```


---


[See on LeetCode.com](https://leetcode.com/problems/convert-binary-number-in-a-linked-list-to-integer/)
