---
title: 345-ReverseVowelsofaString
date: 2016-06-20 16:51:34
tags: leetcode
---

>Write a function that takes a string as input and reverse only the vowels of a string.

>**Example 1:**
Given s = "hello", return "holle".

>**Example 2:**
Given s = "leetcode", return "leotcede".

题目大意：
从左边开始遍历，遇到元音字母，则从右边开始遍历，遇到元音字母，则交换左右元音字母，然后继续从左边开始遍历。

```c++
class Solution {
public:
    bool isVowels(char c) {
        switch(c) {
            case 'a':
            case 'A':
            case 'e':
            case 'E':
            case 'i':
            case 'I':
            case 'o':
            case 'O':
            case 'u':
            case 'U':
                return true;
            default:
                return false;
        }
        return false;
    }
    
    string reverseVowels(string s) {
        if (s.size() <= 0)
            return s;

        int i = 0;
        int j = s.size() - 1;
        int flag = 0;
        while (i < j) {
            if (flag == 0) {
                isVowels(s[i]) ? flag = 1 : i++;
            } else if (flag == 1) {
                if (isVowels(s[j])) {
                    char c = s[i];
                    s[i] = s[j];
                    s[j] = c;
                    i++;
                    j--;
                    flag = 0;
                }
                else
                    j--;
            }
        }
        return s;
    }
};
```
