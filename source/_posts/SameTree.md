---
title: 100. Same Tree
date: 2016-06-08 15:07:01
tags:
---

>Given two binary trees, write a function to check if they are equal or not.

>Two binary trees are considered equal if they are structurally identical and the nodes have the same value.


**1. 递归方式**

```c++
class Solution {
public:
    bool isSameTree(TreeNode* p, TreeNode* q) {
        if (p == NULL && q == NULL)
            return true;
        else if (p == NULL && q != NULL || (p != NULL && q == NULL))
            return false;

        if (q->val != p->val)
            return false;

        if ( ! (isSameTree(p->left,q->left) && isSameTree(p->right,q->right)))
            return false;
        return true;
    }
};
```

**2.非递归广度遍历**

```c++
class Solution {
public:
    bool isSameTree(TreeNode* p, TreeNode* q) {
        if (p == NULL && q == NULL)
            return true;
        else if (p == NULL && q != NULL || (p != NULL && q == NULL))
            return false;

        queue<TreeNode *> pQueue;
        queue<TreeNode *> qQueue;

        pQueue.push(p);
        qQueue.push(q);
        bool result = true;
        while ((! pQueue.empty()) && (! qQueue.empty()))
        {
            if (pQueue.size() != qQueue.size())
            {
                result = false;
                break;
            }

            TreeNode *pNode = pQueue.front();
            TreeNode *qNode = qQueue.front();
            pQueue.pop();
            qQueue.pop();
            if ((pNode->val != qNode->val)
                || (pNode->left == NULL && qNode->left != NULL)
                || (pNode->left != NULL && qNode->left == NULL)
                || (pNode->right == NULL && qNode->right != NULL)
                || (pNode->right != NULL && qNode->right == NULL))
            {
                result = false;
                break;
            }

            if (pNode->left != NULL)
                pQueue.push(pNode->left);
                
            if (qNode->left != NULL)
                qQueue.push(qNode->left);

            if (pNode->right != NULL)
                pQueue.push(pNode->right);

            if (qNode->right != NULL)
                qQueue.push(qNode->right);
        }
        
        if (result && (!pQueue.empty() || !qQueue.empty()))
            result = false;

        return result;

#endif
    }
};
```