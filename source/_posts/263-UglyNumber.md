---
title: 263。 Ugly Number
date: 2016-06-16 11:22:51
tags: leetcode
---

Write a program to check whether a given number is an ugly number.

Ugly numbers are positive numbers whose prime factors only include `2`, `3`, `5`. For example, `6`, `8` are ugly while `14` is not ugly since it includes another prime factor `7`.

Note that `1` is typically treated as an ugly number.

题意分析：
我们把只包含因子2、3和5的数称作丑数（Ugly Number）。例如6、8都是丑数，但14不是，因为它包含因子7。习惯上我们把1当做是第一个丑数。

```c++
class Solution {
public:
    bool isUgly(int num) {
        while (num > 0 && num % 2 == 0)
            num /= 2;
        while (num > 0 && num % 3 == 0)
            num /= 3;
        while (num > 0 && num % 5 == 0)
            num /= 5;
        return num == 1;
    }
};
```
