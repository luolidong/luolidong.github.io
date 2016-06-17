---
title: 202. Happy Number
date: 2016-06-17 16:21:42
tags: leetcode
---

>Write an algorithm to determine if a number is "happy".

>A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers.

>Example: 19 is a happy number

>\\(2^2 + 9^2 = 82\\)
>\\(8^2 + 2^2 = 68\\)
>\\(6^2 + 8^2 = 100\\)
>\\(1^2 + 0^2 + 0^2 = 1\\)

题意分析：
快乐数([happy number](http://baike.baidu.com/link?url=4Of5b_C18F9NILgVFL7fPJDCiAPX8EwE_OHri_bu2hG9DDnRdECXwary2winnPRdbI8JNO_9XfdYHxPz3TZmiDKryGSOQRS_ZjPlne_x09zSV0utsK9Kk47zCq6Qr5LkpU-aS-uN8yllw-kVlrD5ka))有以下的特性：在给定的进位制下，该数字所有数位(digits)的平方和，得到的新数再次求所有数位的平方和，如此重复进行，最终结果必为1。
因此要用set保存每次所有位数平方和之后的sum。如果有重复的，说明进入了循环，直接返回false。 

```c++
class Solution {
public:
    bool isHappy(int n) {
        if (n <= 0)
            return false;
        
        set<int> setSum;
        while (1) {
            int sum = 0;
            while (n > 0) {
                sum += (int)pow(n % 10,2);
                n /= 10;
            }
    
            n = sum;
            
            if (sum == 1)
                return true;
            else if (setSum.find(sum) == setSum.end())
                setSum.insert(sum);
            else
                return false;
        }
        
        
        return false;
    }
};
```