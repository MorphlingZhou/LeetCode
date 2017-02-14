```cpp
class Solution {
public:
vector<vector<int>> levelOrder(TreeNode* root) {
vector<vector<int>> answer;
queue<TreeNode *> stack;
int level = 0;
TreeNode *lastNode = root;

if(!root)
return answer;

stack.push(root);
answer.push_back(vector<int>());

while(!stack.empty())
{
TreeNode *n = stack.front();
stack.pop();

answer[level].push_back(n->val);

if(n->left)
stack.push(n->left);
if(n->right)
stack.push(n->right);

if(n == lastNode)
{
level++;
lastNode = stack.back();
answer.push_back(vector<int>());
}
}
answer.pop_back();

return answer;
}
};
```