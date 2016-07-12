---
title: 9. Palindrome Number
date: 2016-07-11 10:27:56
tags: leetcode
---

>Determine whether an integer is a palindrome. Do this without extra space.

题意分析：
判断一个数字是否为回文数字。

```c++
class Solution {
public:
    bool isPalindrome(int x) {
        if (x < 0)
            return false;
        if (x == 0)
            return true;
        
        int base = 1;
        int n = x;
        while (n /= 10)
            base *= 10;
        
        n = x;
        while (n) {
            int left = n / base;
            int right = n % 10;
            if (left != right)
                return false;
            
            n -= base * left;
            n /= 10;
            base /= 100;
        }
        return true;
    }
};
```
