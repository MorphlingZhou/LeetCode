```cpp
class Solution {
public:

vector<int> postorderTraversal(TreeNode* root) {
        vector<int> path;
        vector<TreeNode *> stack;
        // add the node whose left child tree and right child tree were added
        vector<TreeNode *> color;

        if(root)
            stack.push_back(root);

        while(!stack.empty())
        {
            TreeNode *n = stack.back();

            if(!color.empty())
                if(color.back() == n)
                {
                    path.push_back(n->val);
                    stack.pop_back();
                    color.pop_back();

                    continue;
                }


            int size = stack.size();

            if(n->right)
            {
                stack.push_back(n->right);
                color.push_back(n);
            }

            if(n->left)
            {
                stack.push_back(n->left);
                if(!color.empty())
                {
                    if(color.back() != n)
                        color.push_back(n);
                }
                else
                    color.push_back(n);
            }

            if(size == stack.size())
                color.push_back(n);

        }

        return path;
    }
}
```