---
title: No.10 斐波那契数列
tags: []
---

# No.10 斐波那契数列
## 题目描述
写一个函数，输入 n ，求斐波那契（Fibonacci）数列的第 n 项（即 F(N)）。斐波那契数列的定义如下：

F(0) = 0,   F(1) = 1
F(N) = F(N - 1) + F(N - 2), 其中 N > 1.
斐波那契数列由 0 和 1 开始，之后的斐波那契数就是由之前的两数相加而得出。

答案需要取模 1e9+7（1000000007），如计算初始结果为：1000000008，请返回 1。

## 题解
* ### 自己的解-递归法（待注释）
```c++
class Solution {
public:
    int sum(int m)
    {
        if (m==0)
            return int(0);
        else if (m==1)
            return 1;
        else
        {
            return sum(m-2)+sum(m-1);
        }
        
    }
    int fib(int n) {
        if (n>1)
        {
            int result = sum(n)
            return result;
        }
        else
            return n;
        
    }
};
```
* ### 题解中看到的好的解决方案
### 这个方法算多了两次，但是可以避免处理0和1时用的判断，提高速度
```c++
class Solution {
public:
    int fib(int n) {
        int num_1 = 0;
        int num_2 = 1;
        int sum = num_1 + num_2;
        for (int i=0; i<n; i++)
        {
            num_1 = num_2;
            num_2 = sum;
            sum = (num_1 + num_2)% 1000000007;
        }
        return num_1 ;
        
    }
};
```
## 知识点
* ### 动态规划


## 待解决问题
* ### C++中if和for在运行的时候，是怎么在内存中是怎么调用的（可考虑在群里问老师）
