# No.12 矩阵中的路径

## 题目描述

给定一个 m x n 二维字符网格 board 和一个字符串单词 word 。如果 word 存在于网格中，返回 true ；否则，返回 false 。

单词必须按照字母顺序，通过相邻的单元格内的字母构成，其中“相邻”单元格是那些水平相邻或垂直相邻的单元格。同一个单元格内的字母不允许被重复使用。

 

例如，在下面的 3×4 的矩阵中包含单词 "ABCCED"（单词中的字母已标出）。

![word2](https://assets.leetcode.com/uploads/2020/11/04/word2.jpg)

 

示例 1：

输入：board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCCED"
输出：true
示例 2：

输入：board = [["a","b"],["c","d"]], word = "abcd"
输出：false


提示：

1 <= board.length <= 200
1 <= board[i].length <= 200
board 和 word 仅由大小写英文字母组成

## 题解

* ### 自己的解

```c++
class Solution {
public:
    bool exist(vector<vector<char>>& board, string word) {
        //bool res;
        for(int i=0; i<board.size(); i++)
        {
            for(int j=0; j<board[0].size(); j++)
            {
                if (dfs(i, j, 0, board, word)) return true;
            }
        }
        return false;
    }
    bool dfs(int i, int j, int k,vector<vector<char>>& board, string word)
    {
        if (!(0<=i && i<board.size()) || !(0<=j && j<board[0].size()) || (board[i][j]!=word[k])) return false;
        if (k == (word.size() -1)) return true;
        board[i][j] = '/0';
        bool res = dfs(i, j+1, k+1, board, word) or dfs(i+1, j, k+1, board, word) or dfs(i, j-1, k+1, board, word) or dfs(i-1, j, k+1, board, word);
        board[i][j] = word[k];
        return res;
    }
};
```

## 结果

![image-20210831195710238](/Users/pigd/Library/Application Support/typora-user-images/image-20210831195710238.png)

#### P.S:似乎我的解法都是比较占内存



## 解题思路

### 的



## 知识点

* ### 

  


## 待解决问题

* 