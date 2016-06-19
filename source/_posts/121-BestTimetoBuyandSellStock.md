---
title: 121. Best Time to Buy and Sell Stock
date: 2016-06-19 19:49:25
tags: leetcode
---

>Say you have an array for which the *i^th* element is the price of a given stock on day i.

>If you were only permitted to complete at most one transaction (ie, buy one and sell one share of the stock), design an algorithm to find the maximum profit.

题目大意：
给一个数prices[]，prices[i]代表股票在第i天的售价，求出只做一次交易(一次买入和卖出)能得到的最大收益。

```c++
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int size = prices.size();
        if (size <= 1)
            return 0;
            
        int min = prices[0];
        int ans = 0;
        for (int i = 1; i < size; i++) {
            if (prices[i] < min) min = prices[i];
            else if(prices[i] - min > ans) ans = prices[i] - min;
        }
        return ans;
    }
};
```