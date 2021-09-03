# No.9 用两个栈实现队列
## 题目描述
用两个栈实现一个队列。队列的声明如下，请实现它的两个函数 appendTail 和 deleteHead ，分别完成在队列尾部插入整数和在队列头部删除整数的功能。(若队列中没有元素，deleteHead 操作返回 -1 )

 

示例 1：

输入：
["CQueue","appendTail","deleteHead","deleteHead"]
[[],[3],[],[]]
输出：[null,null,3,-1]
示例 2：

输入：
["CQueue","deleteHead","appendTail","appendTail","deleteHead","deleteHead"]
[[],[],[5],[2],[],[]]
输出：[null,-1,null,null,5,2]


## 题解
* ### 自己的解（待注释）
```c++
class CQueue {
public:
    stack<int> s1;
    stack<int> s2;  //stack的定义
    CQueue() {
        // while (!s1.empty()) {
        //     s1.pop();
        // }
        // while (!s2.empty()) {
        //     s2.pop();
        // }
    }
    
    void appendTail(int value) {
        s1.push(value);     //将元素入栈
    }
    
    int deleteHead() {
        if (s2.empty()){
            if(s1.empty())
                return -1;    //如果两个栈都是空的，那就返回-1
            else
            {
                while(!s1.empty())
                {
                    s2.push(s1.top());   //将1栈的元素分别弹出，再依次入2栈
                    s1.pop();            //但C++需要先取1栈的top元素,再执行pop
                }
            }   
        }
        int result = s2.top();
        s2.pop();
        return result;
    }
};

/**
 * Your CQueue object will be instantiated and called as such:
 * CQueue* obj = new CQueue();
 * obj->appendTail(value);
 * int param_2 = obj->deleteHead();
 */
```
* ### 题解中看到的好的解决方案
```c++
class CQueue {
    stack<int> stack1,stack2;
public:
    CQueue() {
        while (!stack1.empty()) {
            stack1.pop();
        }
        while (!stack2.empty()) {
            stack2.pop();
        }
    }
    
    void appendTail(int value) {
        stack1.push(value);
    }
    
    int deleteHead() {
        // 如果第二个栈为空
        if (stack2.empty()) {
            while (!stack1.empty()) {
                stack2.push(stack1.top());
                stack1.pop();
            }
        } 
        if (stack2.empty()) {
            return -1;
        } else {
            int deleteItem = stack2.top();
            stack2.pop();
            return deleteItem;
        }
    }
};
```
## 解题思路

因为队列是先进的先出，但栈是先进的后出。因此，需要两个栈的配合来实现队列的功能。具体实现流程如下：

1. 元素先依次入a栈
2. a栈再依次将元素弹出
3. b栈依次将a栈弹出的元素入栈，此时b栈内的元素顺序和最开始a栈内的顺序相反
4. 此时再依次将元素从b栈弹出



## 知识点

* ### stack<int'>
    * #### stack::pop() 
    * #### stack::top()
    * #### stack::push()

* ### 


## 待解决问题
* ### stastic定义会影响什么？
* ### 什么时候要用到构造函数？
