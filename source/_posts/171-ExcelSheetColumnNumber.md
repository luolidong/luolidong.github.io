---
title: 171. Excel Sheet Column Number
date: 2016-06-08 16:43:03
tags: leetcode
---

>Related to question Excel Sheet Column Title

>Given a column title as appear in an Excel sheet, return its corresponding column number.

>For example:

>A -> 1
>B -> 2
>C -> 3
>...
>Z -> 26
>AA -> 27
>AB -> 28 


题目分析：

十进制数，按权展开，第一位权为10^0，第二位10^1……以此类推，第N位10^（N-1），该数的数值等于每位位的数值*该位对应的权值之和。因此可以推出此题的算法如下：

```c++
class Solution {
public:
    int titleToNumber(string s) {
        if (s.empty())
            return 0;

        int num = 0;
        int len = s.size();
        for(int i = 0; i < len; i++)
        {
            num += pow(26,len - i - 1) * (s[i] - 'A' + 1);
        }
        return num;
    }
};
```
