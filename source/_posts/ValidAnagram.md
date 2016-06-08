---
title: 242. Valid Anagram
date: 2016-06-08 16:39:06
tags:
---

>Given two strings s and t, write a function to determine if t is an anagram of s.

>For example,
>s = "anagram", t = "nagaram", return true.
>s = "rat", t = "car", return false.


```c++
class Solution {
public:
    bool isAnagram(string s, string t) {
        int a[26] = {0};
        if (s.size() != t.size())
            return false;
        int len = s.size();
        for (int i = 0; i < len; i++)
            a[s[i] - 'a']++;
        for (int i = 0; i < len; i++)
            a[t[i] - 'a']--;
        for (int i = 0; i < 26; i++)
        {
            if (a[i] > 0)
                return false;
        }
        return true;
    }
};
```