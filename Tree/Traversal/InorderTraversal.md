```cpp
class Solution {
public:

vector<int> inorderTraversal(TreeNode* root) {
        vector<int> path;
        vector<TreeNode *> stack;
        vector<TreeNode *> color;

        if (root)
            stack.push_back(root);

        color.push_back(root); // this is a dirty data

        while (!stack.empty())
        {
            TreeNode *n = stack.back();
            if (n->left && n->left != color.back())
                stack.push_back(n->left);
            else
            {
                if (n->left == color.back())
                    color.pop_back();

                path.push_back(n->val);
                stack.pop_back();

                // only set color of the left child tree
                if (!stack.empty())
                    if (stack.back()->left == n)
                        color.push_back(n);

                if (n->right)
                    stack.push_back(n->right);
            }
        }

        return path;
    }
```