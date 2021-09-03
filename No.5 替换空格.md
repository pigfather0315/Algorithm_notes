---
title: 替换空格
tags: []
---

# No.5 替换空格
## 题目描述
请实现一个函数，把字符串 s 中的每个空格替换成"%20"。

 

示例 1：

输入：s = "We are happy."
输出："We%20are%20happy."


## 题解
* ### 自己的解
```c++
class Solution {
public:
    string replaceSpace(string s) {
        int length = s.size();
        vector<int> arr;
        for (int i = 0; i<length; i++)
        {
            if (s[i] == ' ')
            {
                arr.push_back(i);   //保留空格在字符串的位置
            }
        }
        for (int i = 0; i<arr.size();i++)
        {
            s.erase(arr[i]+i*2,1);  //因前面空格被替换后，后面空格的位置就会变化，加上个2*i才能匹配 先删掉空格
            s.insert(arr[i]+i*2, "%20");  //再插入%20
        }
        return s;
    }
};
```
* ### 题解中看到的好的解决方案
```c++
class Solution {
public:
    string replaceSpace(string s) {
        int count = 0; // 统计空格的个数
        int sOldSize = s.size();
        for (int i = 0; i < s.size(); i++) {
            if (s[i] == ' ') {
                count++;
            }
        }
        // 扩充字符串s的大小，也就是每个空格替换成"%20"之后的大小
        s.resize(s.size() + count * 2);
        int sNewSize = s.size();
        // 从后先前将空格替换为"%20"
        for (int i = sNewSize - 1, j = sOldSize - 1; j < i; i--, j--) { //当i=j也就是，空格替换完后跳出循环
            if (s[j] != ' ') {
                s[i] = s[j];
            } else {
                s[i] = '0';
                s[i - 1] = '2';
                s[i - 2] = '%';
                i -= 2;
            }
        }
        return s;
    }
};
```
## 知识点
* ### 字符串的接口
* #### string.erase(位置,长度)
* #### string.insert(位置,“字符串内容”)
* #### string.replace
* ### vector< int>

## 待解决问题
*
