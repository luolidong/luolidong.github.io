---
title: 26. Remove Duplicates from Sorted Array
date: 2016-07-07 11:44:29
tags: leetcode
---

>Given a sorted array, remove the duplicates in place such that each element appear only once and return the new length.

>Do not allocate extra space for another array, you must do this in place with constant memory.

>For example,
Given input array nums = `[1,1,2]`,

>Your function should return length = `2`, with the first two elements of nums being `1` and `2` respectively. It doesn't matter what you leave beyond the new length.


```c++
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int num = 0;
        for (int i = 0; i < nums.size(); i++) {
            if (i == 0)
                num++;
            else if (nums[num - 1] != nums[i]) {
                nums[num] = nums[i];
                num++;
            }
        }
        if (num != nums.size())
            nums.resize(num);
        return num;
    }
};
```