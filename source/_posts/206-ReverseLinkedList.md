---
title: 206. Reverse Linked List
date: 2016-06-12 10:14:41
tags: leetcode
---

> Reverse a singly linked list.

题目分析：

用stack的思想进行反转，依次push，最后栈顶元素为list的头结点。

```c++
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        if (head == NULL)
            return NULL;
            
        ListNode *s = NULL;
        ListNode *p = head;
        while (p != NULL)
        {
            ListNode *q = p->next;
            p->next = s;
            s = p;
            p = q;
        }
        return s;
    }
};
```