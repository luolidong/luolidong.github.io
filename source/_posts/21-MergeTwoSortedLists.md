---
title: 21. Merge Two Sorted Lists
date: 2016-06-20 10:45:21
tags: leetcode
---

>Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

```c++
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        if (l1 == NULL && l2 == NULL)
            return NULL;
        else if (l1 == NULL && l2 != NULL)
            return l2;
        else if (l1 != NULL && l2 == NULL)
            return l1;
            
        ListNode *root = NULL;
        ListNode *pl1 = l1;
        ListNode *pl2 = l2;

        ListNode **p = &root;
        while (pl1 != NULL && pl2 != NULL) {
         if (pl1->val < pl2->val) {
                (*p) = pl1;
                pl1 = pl1->next;
          } else {
               (*p) = pl2;
               pl2 = pl2->next;
          }
          p = &((*p)->next);
        }
        
        if (pl1 != NULL)
            (*p) = pl1;
        
        if (pl2 != NULL)
            (*p) = pl2;

        return root;
    }
};
```
