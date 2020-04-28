# LeetCode JavaScript Solutions



## First Unique Number



**Description:**

You have a queue of integers, you need to retrieve the first unique integer in the queue.

Implement the ```FirstUnique``` class:

- ```FirstUnique(int[] nums)``` Initializes the object with the numbers in the queue.
- ```int showFirstUnique()``` returns the value of the first unique integer of the queue, and returns -1 if there is no such integer.
- ```void add(int value)``` insert value to the queue.
 

**Example 1:**
```
Input: 
["FirstUnique","showFirstUnique","add","showFirstUnique","add","showFirstUnique","add","showFirstUnique"]
[[[2,3,5]],[],[5],[],[2],[],[3],[]]
Output: 
[null,2,null,2,null,3,null,-1]

Explanation: 
FirstUnique firstUnique = new FirstUnique([2,3,5]);
firstUnique.showFirstUnique(); // return 2
firstUnique.add(5);            // the queue is now [2,3,5,5]
firstUnique.showFirstUnique(); // return 2
firstUnique.add(2);            // the queue is now [2,3,5,5,2]
firstUnique.showFirstUnique(); // return 3
firstUnique.add(3);            // the queue is now [2,3,5,5,2,3]
firstUnique.showFirstUnique(); // return -1
```

**Example 2:**
```
Input: 
["FirstUnique","showFirstUnique","add","add","add","add","add","showFirstUnique"]
[[[7,7,7,7,7,7]],[],[7],[3],[3],[7],[17],[]]
Output: 
[null,-1,null,null,null,null,null,17]

Explanation: 
FirstUnique firstUnique = new FirstUnique([7,7,7,7,7,7]);
firstUnique.showFirstUnique(); // return -1
firstUnique.add(7);            // the queue is now [7,7,7,7,7,7,7]
firstUnique.add(3);            // the queue is now [7,7,7,7,7,7,7,3]
firstUnique.add(3);            // the queue is now [7,7,7,7,7,7,7,3,3]
firstUnique.add(7);            // the queue is now [7,7,7,7,7,7,7,3,3,7]
firstUnique.add(17);           // the queue is now [7,7,7,7,7,7,7,3,3,7,17]
firstUnique.showFirstUnique(); // return 17
```

**Example 3:**
```
Input: 
["FirstUnique","showFirstUnique","add","showFirstUnique"]
[[[809]],[],[809],[]]
Output: 
[null,809,null,-1]

Explanation: 
FirstUnique firstUnique = new FirstUnique([809]);
firstUnique.showFirstUnique(); // return 809
firstUnique.add(809);          // the queue is now [809,809]
firstUnique.showFirstUnique(); // return -1
```

**Constraints**

- ```1 <= nums.length <= 10^5```
- ```1 <= nums[i] <= 10^8```
- ```1 <= value <= 10^8```
- At most ```50000``` calls will be made to ```showFirstUnique``` and ```add```.

---


### Solution

Complexity Analysis

- Time complexity : O(n) - Initialize time (where n is the input size), O(1) - Add and Retrieve time


- Space complexity: O(k) - Where k is the number of distinct, unique elements


```JavaScript
FirstUnique = (nums) => {
    // Initialize sets of unique and duplicate values
    this.uniques = new Set()
    this.dupes = new Set()
    
    // add/deletes nums values to their respective Sets
    nums.forEach(n => this.add(n))
}

FirstUnique.prototype.showFirstUnique = function(){
    if (this.uniques.size == 0) return -1      // early return if no uniques
    return this.uniques.keys().next().value    // use iterator to get first unique
}

FirstUnique.prototype.add = function(n){
    if (this.dupes.has(n)) return                           // already duplicate? skip!
    if (!this.uniques.has(n)) return this.uniques.add(n)    // not dupe *or* unique? add and early return

    // handle item needing to be moved from unique list to dupe list
    this.uniques.delete(n)
    this.dupes.add(n)
    return
}

```


---


[See on LeetCode.com](https://leetcode.com/explore/featured/card/30-day-leetcoding-challenge/528/week-1/3287/)
