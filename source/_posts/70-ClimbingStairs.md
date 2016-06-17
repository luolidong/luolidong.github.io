---
title: 70. Climbing Stairs
date: 2016-06-17 14:52:00
tags: leetcode
---

>You are climbing a stair case. It takes n steps to reach to the top.

>Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?


假设有n个阶梯，爬到n有2种方法：
1. 从n-1处爬到n
2. 从n-2处爬到n。

一. 符合递归思想。当n太大的时候，递归层数太多，栈溢出。
```c++
class Solution {
public:
    int climbStairs(int n) {
        if (n <= 0)
            return 0;
        if (n == 1)
            return 1;
        if (n == 2)
            return 2;
        
       return climbStairs(n - 1) + climbStairs(n - 2);
    }
};
```
二. 菲波那切数列
```c++
class Solution {
public:
    int climbStairs(int n) {
        if (n <= 0)
            return 0;
        if (n == 1)
            return 1;
        if (n == 2)
            return 2;
        
        int fir = 1;
        int sec = 2;
        int num = 0;
        for (int i = 3; i <= n; i++) {
            num = fir + sec;
            fir = sec;
            sec = num;
        }
        return num;
    }
};
```