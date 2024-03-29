# No.7 重建二叉树
## 题目描述
输入某二叉树的前序遍历和中序遍历的结果，请构建该二叉树并返回其根节点。

假设输入的前序遍历和中序遍历的结果中都不含重复的数字。

 

示例 1:

![](image-kr253b3y.png)
```
Input: preorder = [3,9,20,15,7], inorder = [9,3,15,20,7]
Output: [3,9,20,null,null,15,7]
```
示例 2:

```
Input: preorder = [-1], inorder = [-1]
Output: [-1]
```

限制：

0 <= 节点个数 <= 5000

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
    
    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) {
        this -> preorder = preorder;   //程序执行时，语句的执行顺序是怎么样的？
        for (int i=0; i<inorder.size(); i++)
        {
            dic[inorder[i]] = i;
        }
        
        return recursion(0, 0, preorder.size()-1);

    }
private:
    vector<int> preorder; //usage? 为什么要定义在private里？ 因为private里的成员函数调用就更方便了，如果在public里定义，则还要多一个this指针
    unordered_map<int, int> dic;
    TreeNode* recursion(int root_pre, int left_boundary, int right_boundary)
    {
        if (left_boundary > right_boundary)  //why not is ==
            return nullptr;
        TreeNode *tree = new TreeNode(preorder[root_pre]);   //结构体的new定义，还有什么方式可以
        //tree -> val = preorder[root_pre];
        int root_in = dic[preorder[root_pre]];
        tree -> left = recursion(root_pre+1, left_boundary, root_in - 1);
        tree -> right = recursion(root_pre+1-left_boundary+root_in, root_in+1, right_boundary);

        return tree;
    }

};
```
## 知识点
* 如何初始化结构体
* 如何定义一个哈希表,unordered_map和map
* public里定义的变量，private可以用吗？
* private里定义的变量，public里要怎么用？
* . -> ::的区别
* vector < int > & 是引用

## 待解决问题
* 叶子节点也要做一次交换吗？
