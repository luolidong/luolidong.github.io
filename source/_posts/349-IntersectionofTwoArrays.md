---
title: 349. Intersection of Two Arrays
date: 2016-06-17 14:38:30
tags: leetcode
---

>Given two arrays, write a function to compute their intersection.

>Example:
Given *nums1* = `[1, 2, 2, 1]`, *nums2* = `[2, 2]`, return `[2]`.

>Note:
Each element in the result must be unique.
The result can be in any order.

题意分析：

这题使用map来选出共有的元素效率比较好。
补充一下：vector的遍历直接通过数组下标是比较效率的，若通过iterator，中间会产生一些消耗。

```c++
class Solution {
public:
    vector<int> intersection(vector<int>& nums1, vector<int>& nums2) {
        map<int,int> mapNums;
        vector<int> nums;
        for (int i = 0; i < nums1.size(); i++) {
            mapNums.insert(make_pair(nums1[i],0));
        }
        
        for (int i = 0; i < nums2.size(); i++) {
            map<int,int>::iterator it = mapNums.find(nums2[i]);
            if (it != mapNums.end())
                it->second++;
        }
        
        for (map<int,int>::iterator it = mapNums.begin(); it != mapNums.end();it++) {
            if (it->second > 0)
                nums.push_back(it->first);
        }
        return nums;
    }
};
```