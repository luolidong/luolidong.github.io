---
title: 102. Binary Tree Level Order Traversal
date: 2016-07-08 09:41:14
tags: leetcode
---

>Given a binary tree, return the level order traversal of its nodes' values. (ie, from left to right, level by level).

>For example:
Given binary tree `[3,9,20,null,null,15,7]`,
```
    3
   / \
  9  20
    /  \
   15   7
```
>return its level order traversal as:
```
[
  [3],
  [9,20],
  [15,7]
]
```

```c++
class Solution {
public:
    void dfs(TreeNode *node,int high,vector<vector<int>> &vec) {
        if (node == NULL)
            return;
            
        if (high + 1 > vec.size())
            vec.resize(high + 1);
        
        vec[high].push_back(node->val);
        dfs(node->left,high + 1,vec);
        dfs(node->right,high + 1,vec);
    }
    
    vector<vector<int>> levelOrder(TreeNode* root) {
        vector<vector<int>> vec;
        dfs(root,0,vec);
        return vec;
    }
};
```