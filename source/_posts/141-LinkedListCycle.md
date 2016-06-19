---
title: 141. Linked List Cycle
date: 2016-06-17 17:32:39
tags: leetcode
---

>Given a linked list, determine if it has a cycle in it.

题意分析：
判断一个链表是否有换。
方法一：遍历每一个节点，并放入set中，若发现set中有相同的节点则说明有环。
方法二：用快慢指针。慢指针的步数是1，快指针步数为2，若存在环则在某一个时刻，快指针等于慢指针。

```c++
class Solution {
public:
    bool hasCycle(ListNode *head) {
        if (head == NULL)
            return false;
        
        ListNode *p = head;
        while (p->next != NULL) {
            if (p->next == head)
                return true;
            p = p->next;
        }
        return false;
    }
};
```
