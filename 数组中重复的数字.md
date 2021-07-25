---
title: 数组中重复的数字
tags: []
---

# No.3 数组中重复的数字
## 题目描述
找出数组中重复的数字。


在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。请找出数组中任意一个重复的数字。

示例 1：

输入：
[2, 3, 1, 0, 2, 5, 3]
输出：2 或 3 


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
    int findRepeatNumber(vector<int>& nums) {
        int length = nums.size();
        int result = -1;
        unordered_map<int, bool> map;
        for(int num:nums)
        {
           if (map[num]) return num;
           map[num] = true;
        }
        return -1;
    }
};
```
## 知识点
* ### vector
* ### unordered set 

## 待解决问题
*
