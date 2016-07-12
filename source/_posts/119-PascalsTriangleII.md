---
title: 119. Pascal's Triangle II
date: 2016-07-11 10:30:51
tags: leetcode
---

>Given an index k, return the kth row of the Pascal's triangle.

>For example, given *k* = 3,
Return `[1,3,3,1]`.

题意分析：
数组从后向前计算

```c++
class Solution {
public:
    vector<int> getRow(int rowIndex) {
        vector<int> result;
        result.resize(rowIndex + 1);
        for (int i = 0; i <= rowIndex; i++) {
            result[i] = 1;
            for (int j = i - 1;j > 0;j--)
                result[j] = result[j] + result[j - 1];
            result[0] = 1;
        }
        return result;
    }
};
```
