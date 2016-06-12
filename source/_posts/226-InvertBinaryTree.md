---
title: 226. Invert Binary Tree
date: 2016-06-07 17:19:27
tags: leetcode
---

>Invert a binary tree.

```
        4
      /   \
     2     7
    / \   / \
   1   3 6   9   
```

to

```
        4
      /   \
     7     2
    / \   / \
   9   6 3   1 
```

**1.递归**

```c++
class Solution {
public:
    TreeNode* invertTree(TreeNode* root) {
        if (root == NULL)
            return NULL;
        TreeNode *tmp = root->left;
        root->left = invertTree(root->right);
        root->right = invertTree(tmp);
    }
};
```

**2.非递归**

```c++
class Solution {
public:
    TreeNode* invertTree(TreeNode* root) {
        if (root == NULL)
            return NULL;
        
        queue<TreeNode *> p;
        p.push(root);
        while (! p.empty())
        {
            TreeNode *node = p.front();
            TreeNode *left = node->left;
            node->left = node->right;
            node->right = left;
            p.pop();
            
            if (node->left != NULL)
                p.push(node->left);
            if (node->right != NULL)
                p.push(node->right);
        }
        return root;
    }
};
```


