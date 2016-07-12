---
title: 112. Path Sum
date: 2016-07-11 10:13:44
tags: leetcode
---

>Given a binary tree and a sum, determine if the tree has a root-to-leaf path such that adding up all the values along the path equals the given sum.

>For example:
Given the below binary tree and `sum = 22`,
```
              5
             / \
            4   8
           /   / \
          11  13  4
         /  \      \
        7    2      1
```
>return true, as there exist a root-to-leaf path `5->4->11->2` which sum is 22.

题意分析：
注意必须是叶子节点的时候才计算是否和sum相等。

```c++
class Solution {
public:
    bool dfs(TreeNode *node,int sumVal,int sum)
    {
        if (node == NULL)
            return false;
        
        if (node->left == NULL && node->right == NULL)
            return sumVal + node->val == sum;
            
        return dfs(node->left,sumVal + node->val ,sum) || dfs(node->right,sumVal + node->val,sum);
    }
    bool hasPathSum(TreeNode* root, int sum) {
        if (root == NULL)
            return false;
            
        return dfs(root,0,sum);
    }
};
```