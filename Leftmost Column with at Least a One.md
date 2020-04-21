# LeetCode JavaScript Solutions



## Leftmost Column with at Least a One



**Description:**

(This problem is an interactive problem.)

A binary matrix means that all elements are ```0``` or ```1```. For each individual row of the matrix, this row is sorted in non-decreasing order.

Given a row-sorted binary matrix binaryMatrix, return leftmost column index(0-indexed) with at least a ```1``` in it. If such index doesn't exist, return ```-1```.

You can't access the Binary Matrix directly.  You may only access the matrix using a ```BinaryMatrix``` interface:

- ```BinaryMatrix.get(x, y)``` returns the element of the matrix at index ```(x, y)``` (0-indexed).
- ```BinaryMatrix.dimensions()``` returns a list of 2 elements ```[n, m]```, which means the matrix is ```n * m```.

Submissions making more than ```1000``` calls to ```BinaryMatrix.get``` will be judged Wrong Answer.  Also, any solutions that attempt to circumvent the judge will result in disqualification.

For custom testing purposes you're given the binary matrix ```mat``` as input in the following four examples. You will not have access the binary matrix directly.

Example 1:
```
Input: mat = [[0,0],[1,1]]
Output: 0
```

Example 2:

```
Input: mat = [[0,0],[0,1]]
Output: 1
```

Example 3:
```
Input: mat = [[0,0],[0,0]]
Output: -1
```

Example 4:
```
Input: mat = [[0,0,0,1],[0,0,1,1],[0,1,1,1]]
Output: 1
```

---


### Solution
Complexity Analysis

- Time complexity: O(M+N), M is number of rows and N is number of columns

- Space complexity: O(1)


```JavaScript
leftMostColumnWithOne = binaryMatrix => {
    // declare rows and columns dimensions within binary matrix
    let [rows, cols] = binaryMatrix.dimensions() 
    
    // start iterating at the first row
    let current_row = 0 
    
    // iterate through the length of the columns
    let current_col = cols - 1
    
    // start iterating at the first row and last column
    while (current_row < rows && current_col >= 0){
        // if the row,col coordinate is 0
        if(binaryMatrix.get(current_row, current_col) == 0){
            // moves down one row in the matrix
            current_row += 1
        } else {
            // moves left one column in the matrix
            current_col -= 1
        }
    }
    // if we have iterated through all the columns
    if(current_col != cols - 1){
        // return the most current column which will be zero, so add 1
        return current_col + 1
    } else {
        // return -1 if no 1's are found within matrix
        return -1
    }
}

```


---


[See on LeetCode.com](https://leetcode.com/explore/featured/card/30-day-leetcoding-challenge/530/week-3/3306)
