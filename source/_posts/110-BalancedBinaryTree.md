---
title: 110. Balanced Binary Tree
date: 2016-07-06 15:22:37
tags: leetcode
---

>Given a binary tree, determine if it is height-balanced.

>For this problem, a height-balanced binary tree is defined as a binary tree in which the depth of the two subtrees of every node never differ by more than 1.

题意分析：
判断树是否为平衡二叉树。左右子树的高度差不大于1。

```c++
class Solution {
public:
    int checkHigh(TreeNode *node) {
        if (node == NULL)
            return 0;
        
        int leftHigh = checkHigh(node->left);
        if (leftHigh == -1)
            return -1;
        
        int rightHigh = checkHigh(node->right);
        if (rightHigh == -1)
            return -1;
        
        if (abs(leftHigh - rightHigh) > 1)
            return -1;
        return max(leftHigh,rightHigh) + 1;
    }
    bool isBalanced(TreeNode* root) {
        if (root == NULL)
            return true;
        return checkHigh(root) != -1;
    }
};
```