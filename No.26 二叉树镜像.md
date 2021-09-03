---
title: 二叉树镜像
tags: []
---

# No.26 二叉树镜像
## 题目描述
请完成一个函数，输入一个二叉树，该函数输出它的镜像。

例如输入：

     4
   /   \
  2     7
 / \   / \
1   3 6   9
镜像输出：

     4
   /   \
  7     2
 / \   / \
9   6 3   1

 

示例 1：

输入：root = [4,2,7,1,3,6,9]
输出：[4,7,2,9,6,3,1]


限制：

0 <= 节点个数 <= 1000

## 题解
```c++
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */

class Solution {
public:
    TreeNode *mirrorTree(TreeNode *root) {
        if (root == nullptr) {
            return nullptr;
        }
        TreeNode* left = mirrorTree(root->left);  //目的是为找到二叉树的左节点
        TreeNode* right = mirrorTree(root->right);  //目的是为找到二叉树的右节点
        root->left = right;  //将二叉树的右节点替换为左节点
        root->right = left;  //将二叉树的左节点替换为右节点
        return root;
    }
};
```
## 解题思路

### 1. 写递归的入口

### 2. 递归返回时需要做的操作

## 知识点

* 二叉树
* c++的结构体
* c++定义指针变量的方式有几种
* 为什么要把返回变量，参数都定义为指针？

## 待解决问题
* 叶子节点也要做一次交换吗？
