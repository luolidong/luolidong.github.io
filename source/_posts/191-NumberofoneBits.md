---
title: 191. Number of 1 Bits
date: 2016-06-15 16:54:12
tags: leetcode
---

Write a function that takes an unsigned integer and returns the number of '1' bits it has (also known as the [Hamming weight](https://en.wikipedia.org/wiki/Hamming_weight)).

For example, the 32-bit integer '11' has binary representation `00000000000000000000000000001011`, so the function should return `3`.

题意分析：
通过&运算来判断每一位是否为1。

方法一：
```c++
class Solution {
public:
    int hammingWeight(uint32_t n) {
        int sum = 0;
        
        for (int i = 0;i < 32;i++) {
            uint32_t num = 1 << i;
            if (num > n)
                break;
            if ((n & num) > 0)
                sum++;
        }
        return sum;
    }
};
```

方法二：
```c++
int hammingWeight(uint32_t n) {
int cant=0;
while(n){
    if(n&1){
        cant++;
    }
    n=n>>1;
}   
return cant;
}
```
