---
title: 292 Nim Game
date: 2016-06-07 14:28:15
tags: leetcode
---
>You are playing the following Nim Game with your friend: >There is a heap of stones on the table, each time one of  >you take turns to remove 1 to 3 stones. The one who >removes the last stone will be the winner. You will take >the first turn to remove the stones.

>Both of you are very clever and have optimal strategies >for the game. Write a function to determine whether you >can win the game given the number of stones in the heap.

>For example, if there are 4 stones in the heap, then you >will never win the game: no matter 1, 2, or 3 stones you >remove, the last stone will always be removed by your >friend.

**题目大意：**

你和朋友正在玩一个叫做Nim Game的游戏。有一堆石头在桌子上，每一次可以拿走1到3个石头。最后一个拿走石头的是赢家。你第一次拿走石头。
假设有4个石头，那么无论你怎么拿去1,2,3个石头，最后总是你的朋友移去最后的石头。

**解题思想：**

根据题意可以判断如果石头的个数为4的倍数的话，那么赢家都是你的朋友。

**代码如下：**

```c++
class Solution {
public:
    bool canWinNim(int n) {
        if (n < 4)
            return true;
        else
            return !(n % 4 == 0);
    }
};
```
