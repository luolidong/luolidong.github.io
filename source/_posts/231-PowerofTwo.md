---
title: 231. Power of Two
date: 2016-06-16 10:00:45
tags: leetcode
---

>Given an integer, write a function to determine if it is a power of two.

题意分析：

通过计算可以知，当n = 30时，pow（2，n）为int型最大的数。

```c++
class Solution {
public:
    bool isPowerOfTwo(int n) {
        return (n <= 0) ? false : ((int)pow(2,30) % n == 0);
    }
};
```