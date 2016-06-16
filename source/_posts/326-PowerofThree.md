---
title: 326. Power of Three
date: 2016-06-16 09:45:09
tags: leetcode
---

>Given an integer, write a function to determine if it is a power of three.

题意分析：

n^m，n叫做幂，m叫做次方。32位int型，当n == 19是，3^n最大。
因此要判断一个数num是否为a power of three，可以通过3 ^ n % num。

```c++
class Solution {
public:
    bool isPowerOfThree(int n) {
        return n <= 0 ? false : (((int)pow(3,19)) % n == 0);
    }
};
```
