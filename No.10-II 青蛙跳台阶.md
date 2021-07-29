# No.10-II 青蛙跳台阶问题

## 题目描述

一只青蛙一次可以跳上1级台阶，也可以跳上2级台阶。求该青蛙跳上一个 n 级的台阶总共有多少种跳法。

答案需要取模 1e9+7（1000000007），如计算初始结果为：1000000008，请返回 1。

示例 1：

输入：n = 2
输出：2
示例 2：

输入：n = 7
输出：21
示例 3：

输入：n = 0
输出：1
提示：

0 <= n <= 100



## 题解

* ### 自己的解-带备忘录的递归法（待注释）

```c++
class Solution {
public:
    // int numWays(int n) {
        
    // }
    unordered_map<int, int> memory;
    int count = 0;
    int numWays(int l)
    {
        if (memory.count(l) != 0)   //avoid calculate repeatedtly
            return memory[l];
        if(l==0)
        {
            count++;
            return count;
        }
        if (l >= 2)
            memory[l-2] = numWays(l-2);
        memory[l-1] = numWays(l-1);
        //memory[l] = count;
        return (memory[l-1] + memory[l-2]) % 1000000007;

    }


};
```

* ### 题解中看到的好的解决方案

```c++
class Solution {
public:
	int numWays(int n) {
		int a = 0, b = 1, c = 1;
		for (int i = 0; i<n; ++i)
		{
			a = b; b = c;
			c = (a + b) % 1000000007;
		}
		return b;
	}
};

作者：TeFuirnever
链接：https://leetcode-cn.com/problems/qing-wa-tiao-tai-jie-wen-ti-lcof/solution/jian-zhi-offercban-ben-xi-lie-jian-zhi-o-1tzi/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```

## 结果

![image-20210728100951363](/Users/pigd/Library/Application Support/typora-user-images/image-20210728100951363.png)

## 解题思路

### 单节点的跳法总数计算问题可分为两个节点的问题，如5个台阶可以拆分为3个台阶的所有跳法+4个台阶的所有跳法，以此类推



## 知识点

* ### 动态规划

* ### Unordered_map

* ### 递归转迭代


## 待解决问题

* ### 