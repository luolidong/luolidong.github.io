---
title: 104. Maximum Depth of Binary Tree
date: 2016-06-07 16:39:03
tags: leetcode
---

>Given a binary tree, find its maximum depth.

>The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.


**1. 深度遍历**

```c++
class Solution {
public:
    int maxDepth(TreeNode* root) {
        if (root == NULL)
            return 0;
        return max(maxDepth(root->left),maxDepth(root->right)) + 1;
    }
};
```

**2. 广度遍历**

```c++
class Solution {
public:
    int maxDepth(TreeNode *root)
    {
        if (root == NULL)
            return 0;
            
        queue<TreeNode *> p;
        p.push(root);
        int depth = 0;
        while (!p.empty())
        {
            depth++;
            int count = p.size();
            for (int i = 0; i < count; i++)
            {
                TreeNode *tmp = p.front();
                if (tmp->left != NULL)
                    p.push(tmp->left);
                
                if (tmp->right != NULL)
                    p.push(tmp->right);
                p.pop();
            }
            
        }
        return depth;
    }
};
```
