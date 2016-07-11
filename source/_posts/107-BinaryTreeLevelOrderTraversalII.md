---
title: 107. Binary Tree Level Order Traversal II
date: 2016-06-22 10:11:09
tags: leetcode
---

>Given a binary tree, return the bottom-up level order traversal of its nodes' values. (ie, from left to right, level by level from leaf to root).

>For example:
Given binary tree `[3,9,20,null,null,15,7]`,
```
      3
     / \
    9   20
        / \
       15  7
```
>return its bottom-up level order traversal as:
```
[
  [15,7],
  [9,20],
  [3]
]
```

一 递归
```c++
class Solution {
    void travel(TreeNode *node,vector<vector<int>> &vec,int hight)
    {
        if (node == NULL)
            return;
        
        travel(node->left,vec,hight + 1);
        travel(node->right,vec,hight + 1);
        
        if (hight + 1 > vec.size())
        {
            vec.resize(hight + 1);
        }
        vec[hight].push_back(node->val);
    }
public:
    vector<vector<int>> levelOrderBottom(TreeNode* root) {
        vector<vector<int> > v;
        travel(root,v,0);
        reverse(v.begin(),v.end());
        return v;
    }
};
```

二 用双队列
```c++
class Solution {
public:
    vector<vector<int>> levelOrderBottom(TreeNode* root) {
        vector<vector<int> > v;
        vector<int> in;
        queue<TreeNode *> one;
        queue<TreeNode *> two;
        
        if (root == NULL)
            return v;

        one.push(root);
        in.clear();
        in.push_back(root->val);
        v.push_back(in);
        while (!one.empty() || !two.empty()) {
            in.clear();
            
            if (!one.empty())
            {
                while(!one.empty()) {
                    TreeNode *p = one.front();
                    one.pop();
                    if (p->left != NULL) {
                        two.push(p->left);
                        in.push_back(p->left->val);
                    }
                    if (p->right != NULL) {
                        two.push(p->right);
                        in.push_back(p->right->val);
                    }
                }
            } else {
                while(!two.empty()) {
                    TreeNode *p = two.front();
                    two.pop();
                    if (p->left != NULL) {
                        one.push(p->left);
                        in.push_back(p->left->val);
                    }
                    if (p->right != NULL) {
                        one.push(p->right);
                        in.push_back(p->right->val);
                    }
                }
            }

            if (in.size() > 0)
                v.push_back(in);
        }
        reverse(v.begin(),v.end());
        return v;
    }
};
```
