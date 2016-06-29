---
title: 342. Power of Four
date: 2016-06-29 14:34:22
tags: leetcode
---

>Given an integer (signed 32 bits), write a function to check whether it is a power of 4.

>Example:
Given num = 16, return true. Given num = 5, return false.

题意分析：
一个数是否为4的次方可以通过以下方法判断：
1. 4的二进制位100 & 011 等于 0
2. num - 1 % 3 等于 0

```c++
class Solution {
public:
    bool isPowerOfFour(int num) {
        return (num > 0) && ((num & (num - 1)) == 0) && ((num - 1) % 3 == 0);
    }
};
```
