---
title: 66. Plus One
date: 2016-06-29 15:28:24
tags: leetcode
---

>Given a non-negative number represented as an array of digits, plus one to the number.

>The digits are stored such that the most significant digit is at the head of the list.

题目大意：
用一个数组存放一个非负整数，给这个数加1。结果还是用数组表示，数组头为高位。

```c++
class Solution {
public:
    vector<int> plusOne(vector<int>& digits) {
        vector<int> num;

        int plus = 1;
        for (int i = digits.size() - 1; i >= 0; i--) {
            if (digits[i] + plus == 10) {
                num.push_back(0);
                plus = 1;
            } else {
                num.push_back(digits[i] + plus);
                plus = 0;
            }
        }
        
        if (plus == 1)
            num.push_back(plus);
        reverse(num.begin(),num.end());
        return num;
    }
};
```