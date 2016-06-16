---
title: 344. Reverse String
date: 2016-06-16 14:05:54
tags:
---

>Write a function that takes a string as input and returns the string reversed.

>Example:
Given s = "hello", return "olleh".

```c++
class Solution {
public:
    string reverseString(string s) {
        string str = s;
        int i = 0;
        int j = str.size() - 1;
        for (; i < j; i++,j--) {
            char c = str[i];
            str[i] = str[j];
            str[j] = c;
        }
        return str;
    }
};
```