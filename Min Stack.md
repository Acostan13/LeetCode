# LeetCode JavaScript Solutions



## Min Stack



**Description:**

Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

- push(x) -- Push element x onto stack.
- pop() -- Removes the element on top of the stack.
- top() -- Get the top element.
- getMin() -- Retrieve the minimum element in the stack.

Example 1:
```
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin();   --> Returns -3.
minStack.pop();
minStack.top();      --> Returns 0.
minStack.getMin();   --> Returns -2.
```

---


### Initial Solution
Complexity Analysis

- Time complexity : O(n) - Linear Time

- Space complexity: O(1) - Constant Space


```JavaScript
var MinStack = function() {
    this.stack = []
}

MinStack.prototype.push = function(x) {
    this.stack.push(x)
}

MinStack.prototype.pop = function() {
    return this.stack.pop()
}

MinStack.prototype.top = function() {
    return this.stack[this.stack.length - 1]
}

MinStack.prototype.getMin = function() {
    let min_value = this.stack[0]
    for(i=0;i<this.stack.length;i++){
        if(this.stack[i] < min_value){
            min_value = this.stack[i]
        }
    }
    return min_value
}
```

### Optimized Solution
Complexity Analysis

- Time complexity : O(1) - Constant Time

- Space complexity: O(1) - Constant Space

```JavaScript
var MinStack = function() {
    this.minStack = []
    this.stack = []
}

MinStack.prototype.push = function(x) {
    this.stack.push(x)
    if(this.minStack.length === 0 || x <= this.minStack[this.minStack.length - 1]) {
        this.minStack.push(x) // pushes x to minstack if it is <= the minimum value of minStack
    }
}

MinStack.prototype.pop = function() {
    let x = this.stack.pop()
    if(x === this.minStack[this.minStack.length - 1]){
        this.minStack.pop()
    }
}

MinStack.prototype.top = function() {
    return this.stack[this.stack.length - 1]
}

MinStack.prototype.getMin = function() {
    return this.minStack[this.minStack.length - 1]
}
```

---


[See on LeetCode.com](https://leetcode.com/explore/featured/card/30-day-leetcoding-challenge/529/week-2/3292/)
