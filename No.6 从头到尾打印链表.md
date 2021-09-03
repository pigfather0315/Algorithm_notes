# No.6 从头到尾打印链表
## 题目描述
输入一个链表的头节点，从尾到头反过来返回每个节点的值（用数组返回）。

 

示例 1：

输入：head = [1,3,2]
输出：[2,3,1] 


## 题解
```c++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */

class Solution {
public:
    vector<int> reversePrint(ListNode* head) {
        if (head == nullptr){
            vector<int> a;
            return a;
        }
        vector<int> numbers = reversePrint(head->next);
        numbers.push_back(head->val);
        return numbers;

    }
};
```


## 解题思路

#### 本题采用递归的思路，通过不断调用自身，一直找到链表的最末端，然后返回一个新定义的数组，并在掉头过程中，不断从尾到头将数存入数组(push_back)，函数结束就返回数组 



## 知识点

* ### 递归 



## 待解决问题

* ### 内存占用是否可以通过不定义a数组来优化？
![](image-kq7i546m.png)
