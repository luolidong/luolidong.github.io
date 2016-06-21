---
title: 198-HouseRobber
date: 2016-06-21 15:41:44
tags: leetcode
---

>You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security system connected and it will automatically contact the police if two adjacent houses were broken into on the same night.

>Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight without alerting the police.

题目大意：
你是一名专业强盗，计划沿着一条街打家劫舍。每间房屋都储存有一定数量的金钱，唯一能阻止你打劫的约束条件就是：由于房屋之间有安全系统相连，如果同一个晚上有两间相邻的房屋被闯入，它们就会自动联络警察，因此不可以打劫相邻的房屋。

题目分析：

动态规划：

dp[i] = max(dp[i - 1], dp[i - 2] + num[i - 1])

其中，dp[i]表示打劫到第i间房屋时累计取得的金钱最大值。

```c++
class Solution {
public:
    int max(int a,int b) {
        return a > b ? a : b;
    }

    int rob(vector<int>& nums) {
        if (nums.size() == 0)
            return 0;
            
        int prepre = 0;
        int pre = nums[0];
        for (int i = 1; i < nums.size(); i++) {
            int cur = max(prepre + nums[i], pre);
            prepre = pre;
            pre = cur;
        }
        return pre;
    }
};
```
