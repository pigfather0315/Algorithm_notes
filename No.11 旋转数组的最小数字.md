# No.11-旋转数组的最小数字

## 题目描述

把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。输入一个递增排序的数组的一个旋转，输出旋转数组的最小元素。例如，数组 [3,4,5,1,2] 为 [1,2,3,4,5] 的一个旋转，该数组的最小值为1。  

示例 1：

输入：[3,4,5,1,2]
输出：1
示例 2：

输入：[2,2,2,0,1]
输出：0



## 题解

*  ### 尝试写二分法得到的错误解

```c++
class Solution {
public:
    int minArray(vector<int>& numbers) {
        int length = numbers.size();
        int pos = length / 2;
        int interval = pos / 2; 
        int flag = numbers[0];
        if (length == 1)
            return flag;
        else
        {
            if (flag < numbers[length-1])
                return flag;
            while(numbers[pos-1]<=numbers[pos])
            {
                if(numbers[pos] >= flag)
                    {
                        pos = pos + interval;
                        interval = interval /2;
                    }
                else if(numbers[pos] < flag)
                    {
                        pos = pos - interval;
                        interval = interval /2;
                    }
            }
            return numbers[pos];
        }
        
    }
};
```

* ### 再次尝试的解

```c++
class Solution {
public:
    int minArray(vector<int>& numbers) {
        int pos = numbers.size() - 1;
        int min_num = numbers[pos];
        for(int i = pos; i>=0; i--)
        {
            if (numbers[i]<min_num) min_num = numbers[i];
            if (numbers[i]>min_num) break;
        }
        return min_num;
        }
        
    
};
```



## 结果

![image-20210804161401922](/Users/pigd/Library/Application Support/typora-user-images/image-20210804161401922.png)

#### P.S:似乎我的解法都是比较占内存



## 解题思路

### 的



## 知识点

* ### 

  


## 待解决问题

* 