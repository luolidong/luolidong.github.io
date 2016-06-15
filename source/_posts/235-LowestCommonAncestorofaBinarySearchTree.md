---
title: 235. Lowest Common Ancestor of a Binary Search Tree
date: 2016-06-15 11:54:14
tags: leetcode
---

>Given a binary search tree (BST), find the lowest common ancestor (LCA) of two given nodes in the BST.

>According to the [definition of LCA on Wikipedia](https://en.wikipedia.org/wiki/Lowest_common_ancestor): “The lowest common ancestor is defined between two nodes v and w as the lowest node in T that has both v and w as descendants (where we allow **a node to be a descendant of itself**).”

>           6
>        /     \
>       2       8
>      / \     / \
>     0   4   7   9
>        / \
>       3   5

>For example, the lowest common ancestor (LCA) of nodes `2` and `8` is `6`. Another example is LCA of nodes `2` and `4` is `2`, since a node can be a descendant of itself according to the LCA definition.

题意分析：

BST（二叉搜索树）的定义，BST是满足如下3个条件的二叉树：
1. 节点的左子树包含的节点的值小于该节点的值
2. 节点的右子树包含的节点的值大于等于该节点的值
3. 节点的左子树和右子树都是BST

LCA（最近公共祖先）的定义：
对于有根树T的两个结点u、v，最近公共祖先LCA(T,u,v)表示一个结点x，满足x是u、v的祖先且x的深度尽可能大。

若root == p or root == q，则root为LCA。
若 root < min(p,q),则LCA在root的右子树上。
若 root > max(p,q),则LCA在root的左子树上。
若 min（p,q）< root < max(p,q),则LCA为root。

```c++
class Solution {
public:
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        if (root == NULL || p == NULL || q == NULL)
            return NULL;
        
        int min = p->val > q->val ? q->val : p->val;
        int max = p->val > q->val ? p->val : q->val;
        
        if (root->val < min)
            return lowestCommonAncestor(root->right,p,q);
        else if (root->val > max)
            return lowestCommonAncestor(root->left,p,q);
        
        return root;
    }
};
```



