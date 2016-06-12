---
title: 169. Majority Element
date: 2016-06-12 09:54:36
tags: leetcode
---

>Given an array of size n, find the majority element. The majority element is the element that appears **more than** `⌊ n/2 ⌋` times.

>You may assume that the array is non-empty and the majority element always exist in the array.

题目分析：

要求出现次数超过整个数组一般以上的数，只要依次比较每一个数并计数，若count = 0，则记录元素n；若count > 0，该数和n相同则count+１，不同则　count-1.
 
```c++
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        int count = 0;
        int n = 0;
        
        for (auto it = nums.begin();it != nums.end(); it++)
        {
            if (count == 0)
            {
                count = 1;
                n = *it;
            }
            else {
                if (n == *it)
                    count++;
                else
                    count--;
            }
        }
        return n;
    }
};
```
