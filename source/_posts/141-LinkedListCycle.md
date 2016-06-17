---
title: 141. Linked List Cycle
date: 2016-06-17 17:32:39
tags: leetcode
---

>Given a linked list, determine if it has a cycle in it.

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
