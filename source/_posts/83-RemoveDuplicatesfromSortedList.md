---
title: 83. Remove Duplicates from Sorted List
date: 2016-06-16 10:11:45
tags: leetcode
---

>Given a sorted linked list, delete all duplicates such that each element appear only once.

For example,
Given `1->1->2`, return `1->2`.
Given `1->1->2->3->3`, return `1->2->3`.

```c++
class Solution {
public:
    ListNode* deleteDuplicates(ListNode* head) {
        if (head != NULL) {
            ListNode *p = head;
            while (p->next != NULL) {
                int val = p->val;
                if (val == p->next->val) {
                    ListNode *tmp = p->next;
                    p->next = p->next->next;
                    free(tmp);
                } else {
                    p = p->next;
                }
            }
        }
        return head;
    }
};
```