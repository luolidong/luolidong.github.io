---
title: 350. Intersection of Two Arrays II
date: 2016-07-06 10:15:33
tags: leetcode
---

>Given two arrays, write a function to compute their intersection.

>Example:
Given *nums1* = `[1, 2, 2, 1]`, *nums2* = `[2, 2]`, return `[2, 2]`.

>Note:
Each element in the result should appear as many times as it shows in both arrays.
The result can be in any order.

题意分析：
选出2个数组相同的元素，有多少个选多少个。

```c++
class Solution {
public:
    vector<int> intersect(vector<int>& nums1, vector<int>& nums2) {
       vector<int> result;
       sort(nums1.begin(),nums1.end());
       sort(nums2.begin(),nums2.end());
       
       for (int i = 0,j = 0; i < nums1.size() && j < nums2.size();) {
           if (nums1[i] == nums2[j]) {
               result.push_back(nums1[i]);
               i++;
               j++;
           } else if (nums1[i] > nums2[j])
                j++;
            else
                i++;
       }
       return result;
    }
};
```
