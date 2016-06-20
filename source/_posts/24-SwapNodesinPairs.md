---
title: 24-SwapNodesinPairs
date: 2016-06-20 16:23:48
tags: leetcode
---

>Given a linked list, swap every two adjacent nodes and return its head.

>For example,
Given `1->2->3->4`, you should return the list as `2->1->4->3`.

>Your algorithm should use only constant space. You may not modify the values in the list, only nodes itself can be changed.


```c++
class Solution {
public:
    ListNode* swapPairs(ListNode* head) {
        if (head == NULL || head->next == NULL)
            return head;
        
        ListNode *root = head->next;
        head->next = root->next;
        root->next = head;
        
        ListNode *p = root->next;
        while (p->next != NULL && p->next->next != NULL) {
            ListNode *one = p->next;
            p->next = one->next;
            one->next = p->next->next;
            p->next->next = one;
            p = p->next->next;
        }
        
        return root;
    }
};
```