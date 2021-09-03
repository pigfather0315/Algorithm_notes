# No.13 机器人的运动范围

## 题目描述

地上有一个m行n列的方格，从坐标 [0,0] 到坐标 [m-1,n-1] 。一个机器人从坐标 [0, 0] 的格子开始移动，它每次可以向左、右、上、下移动一格（不能移动到方格外），也不能进入行坐标和列坐标的数位之和大于k的格子。例如，当k为18时，机器人能够进入方格 [35, 37] ，因为3+5+3+7=18。但它不能进入方格 [35, 38]，因为3+5+3+8=19。请问该机器人能够到达多少个格子？

 

示例 1：

输入：m = 2, n = 3, k = 1
输出：3
示例 2：

输入：m = 3, n = 1, k = 0
输出：1

## 题解

* ### 自己之前尝试错误的解，无法跳出递归

```c++
class Solution {
public:
    int movingCount(int m, int n, int k) {
        return dfs(0, 0, 1, k, m, n, visited);
    }
    int cal(int num)
    {
        if (num < 10)
            return num;
        else
            return num / 10 + num % 10;
    }
    int dfs(int x, int y, int count, int limit, int m ,int n)
    {
        if (!(0<=x && x< m) || !(0<=y && y<n) || (cal(x) + cal(y))> limit || visited[x][y])
            return 0;
        count += dfs(x, y+1, count, limit, m, n) + dfs(x+1, y, count, limit, m, n) + dfs(x, y-1, count, limit, m, n) + dfs(x-1, y, count, limit, m, n);
        return count;
        
    }

};
```

* ### 看了题解后修改的解

```c++
class Solution {
public:
    int movingCount(int m, int n, int k) {
        vector<vector<bool>> visited(m, vector<bool>(n, 0)); //定义一个可达矩阵
        return dfs(0, 0, 1, k, m, n, visited);

    }
    int cal(int num)
    {
        if (num < 10)
            return num;
        else
            return num / 10 + num % 10;
    }
    int dfs(int x, int y, int count, int limit, int m ,int n, vector<vector<bool>> &visited)
    {
        if (!(0<=x && x< m) || !(0<=y && y<n) || (cal(x) + cal(y))> limit || visited[x][y])
            return 0;
        visited[x][y] = true;
        count += dfs(x, y+1, count, limit, m, n, visited) + dfs(x+1, y, count, limit, m, n, visited) + dfs(x, y-1, count, limit, m, n, visited) + dfs(x-1, y, count, limit, m, n, visited);
        return count;
        
    }

};
```





## 结果

![image-20210831215917010](/Users/pigd/Library/Application Support/typora-user-images/image-20210831215917010.png)



## 解题思路



## 知识点

* ### 即使设置了跳出条件也一样会无穷递归的情况

* ### 引用的写法

  


## 待解决问题

* 

