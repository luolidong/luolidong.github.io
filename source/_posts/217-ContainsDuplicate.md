---
title: 217. Contains Duplicate
date: 2016-06-12 10:06:39
tags: leetcode
---

>Given an array of integers, find if the array contains any duplicates. Your function should return true if any value appears at least twice in the array, and it should return false if every element is distinct.

题目分析：

要找出一个数组中是否有重复的元素，可以同set或者map等数据结构进行处理。

```c++
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        set<int> a;
        for (auto it = nums.begin(); it != nums.end(); it++)
        {
            if (a.find(*it) == a.end())
                a.insert(*it);
            else
                return true;
        }
        return false;
    }
};
```