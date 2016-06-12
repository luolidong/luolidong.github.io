---
title: 283. Move Zeroes
date: 2016-06-08 10:56:41
tags: leetcode
---

>Given an array `nums`, write a function to move all `0`'s to >the end of it while maintaining the relative order of the >non-zero elements.

>For example, given `nums = [0, 1, 0, 3, 12]`, after calling >your function, `nums` should be `[1, 3, 12, 0, 0]`.

**题意：**

给一组数，把0都移动到数组后方。

```c++
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        int pos = 0;
        for (int i = 0; i < nums.size(); i++)
        {
            if (nums[i] != 0)
                nums[pos++] = nums[i];
        }
        
        for (int i = pos; i < nums.size(); i++)
            nums[i] = 0;
    }
};
```
