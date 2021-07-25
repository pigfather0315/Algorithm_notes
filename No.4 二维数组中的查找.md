---
title: No.4 二维数组中的查找
tags: []
---

# No.4 二维数组中的查找
## 题目描述
在一个 n * m 的二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个高效的函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。

 

示例:

现有矩阵 matrix 如下：

[
  [1,   4,  7, 11, 15],
  [2,   5,  8, 12, 19],
  [3,   6,  9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30]
]
给定 target = 5，返回 true。

给定 target = 20，返回 false。

 

限制：

0 <= n <= 1000

0 <= m <= 1000

## 题解
* ### 自己的解（待注释）
```c++
public:
    bool findNumberIn2DArray(vector<vector<int>>& matrix, int target) { 
        for (int i = 0; i<matrix.size(); i++)
        {
            for (int j = 0; j<matrix[i].size(); j++)
            {
                if (matrix[i][j] == target)
                    return true;
                if (matrix[i][j] > target)
                    break;
            }
        }
        return false;
        
    }
};
```
![](image-kqdi8286.png)

* ### 题解中看到的好的解决方案
### 这个方法的起始位置不一样，而且是二维的变化，更灵活，但我的快一些

```c++
class Solution {
public:
    bool findNumberIn2DArray(vector<vector<int>>& matrix, int target) {
        int i = matrix.size() - 1, j = 0;
        while(i >= 0 && j < matrix[0].size())
        {
            if(matrix[i][j] > target) i--;
            else if(matrix[i][j] < target) j++;
            else return true;
        }
        return false;
    }
};
```
![](image-kqdi77ok.png)

作者：jyd
链接：https://leetcode-cn.com/problems/er-wei-shu-zu-zhong-de-cha-zhao-lcof/solution/mian-shi-ti-04-er-wei-shu-zu-zhong-de-cha-zhao-zuo/

## 知识点
* ### 遍历的时候可以多换下思路
* ### 二维vector的遍历
* ### 二维vector的尺寸获取
* ### C++与操作是 &&

## 待解决问题
