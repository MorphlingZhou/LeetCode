```cpp
class Solution 
{
public:
    vector<int> preorderTraversal(TreeNode* root) {
        vector<TreeNode *> stack;
        vector<int> path;

        if(root)
            stack.push_back(root);

        while(!stack.empty())
        {
           TreeNode *n = stack.back();
           path.push_back(n->val);
           stack.pop_back();               

           if(n->right)
                stack.push_back(n->right);
           if(n->left)
                stack.push_back(n->left);
        }

        return path;
    }
}
```