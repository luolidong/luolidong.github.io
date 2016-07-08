---
title: 118. Pascal's Triangle
date: 2016-07-06 17:45:57
tags: leetcode
---

Given numRows, generate the first numRows of Pascal's triangle.

For example, given *numRows* = 5,
Return

```
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]
```

```c++
class Solution {
public:
    vector<vector<int>> generate(int numRows) {
        vector<vector<int>> result;
        
        if (numRows != 0) {
            for (int i = 0; i < numRows; i++) {
                vector<int> nums;
                for (int j = 0; j <= i; j++) {
                    if (j == 0 or j == i)
                        nums.push_back(1);
                    else
                        nums.push_back(result[i - 1][j - 1] + result[i - 1][j]);
                }
                result.push_back(nums);
            }
        }
        return result;
    }
};
```
