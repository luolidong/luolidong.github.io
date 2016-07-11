---
title: 172. Factorial Trailing Zeroes
date: 2016-07-08 15:17:08
tags: leetcode
---

>Given an integer n, return the number of trailing zeroes in *n*!.

>Note: Your solution should be in logarithmic time complexity.

```c++
class Solution {
public:
    int trailingZeroes(int n) {
        int res = 0;
        while (n) {
            res += n / 5;
            n /= 5;
        }
        return res;
    }
};
```