### 二叉树的遍历

* 非递归遍历
    - 先序遍历
    - 中序遍历
    - 后序遍历

---

* 二叉树的遍历的总结:
实现这个功能需要三块内存空间
1.存储输出
2.存储待访问节点的堆栈
3.存储着色节点的堆栈(先序不用)

* 先序(DLR)
取出节点,直接访问后弹出
如果有右子树, 压入右子树的根节点
如果有左子树, 压入左子树的根节点
终止条件:
待访问节点的堆栈为空

* 中序(LDR)
和先序不同的是, 节点在待访问节点的堆栈中会被访问两次
第一次是压入当前节点的左子树根节点
第二次是当前节点左子树被中序遍历完成
为了区分这两种情况, 需要对当前节点的左子树根节点着色
仅在第二种情况下,才访问节点的值之后弹出, 之后再压入右子树根节点
终止条件:
待访问节点的堆栈为空

* 后序(LRD)
节点在待访问节点的堆栈中会被访问两次
第一次是压入当前节点的左子树根节点和右子树根节点
第二次是当前节点左子树被后序遍历完成且当前节点右子树被后序遍历完成
这时候,如果对当前节点的子节点着色,就会显得很混乱
我的思路是在第一次压入的时候就对当前节点着色
如果当前的节点是叶子节点那么也进行着色
这样在第二次访问的时候,我就明确的可以知道,现在我应该访问当前节点的值
而不是再一次的去后序遍历其左右子树
对于后序还有一个技巧:
可以选择先序的变种访问(DRL)
之后再把输出中的内容反序输出, 就可以得到所要的答案了
终止条件:
待访问节点的堆栈为空
还有比较暴力点的手法是在节点当中存入着色变量
```cpp
struct TreeNode
{
     TreeNode *left;
     TreeNode *right;
     int val;
     bool dirty; // 着色变量
     TreeNode(int x) : val(x), left(NULL), right(NULL) {};
};
```
这样的话算法很好写,但是通常这是得不偿失的,因为额外的内存开销
通常会比着色堆栈的大小大得多

---

* 递归遍历