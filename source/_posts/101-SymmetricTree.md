---
title: 101. Symmetric Tree
date: 2016-06-29 15:48:40
tags: leetcode
---

>Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).

>For example, this binary tree `[1,2,2,3,4,4,3]` is symmetric:
```
        1
      /   \
     2     2
    / \   / \
   3   4 4   3  
```
But the following `[1,2,2,null,3,null,3]` is not:
```
    1
   / \
  2   2
   \   \
   3    3
```


```c++
class Solution {
public:
    bool dfs(TreeNode *node1,TreeNode *node2) {
        if (node1 == NULL && node2 == NULL)
            return true;
        else if (node1 == NULL || node2 == NULL)
            return false;
        else if (node1->val != node2->val)
            return false;
        
        return dfs(node1->left,node2->right) && dfs(node1->right,node2->left);
    }
    
    bool isSymmetric(TreeNode* root) {
        if (root == NULL)
            return true;
        return dfs(root->left,root->right);
    }
};
```
