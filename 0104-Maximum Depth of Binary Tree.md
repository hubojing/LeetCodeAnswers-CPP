求二叉树的深度，思路就是递归。
```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution
{
public:
    int maxDepth(TreeNode *root)
    {
        if (root == NULL)
        {
            return 0;
        }
        return max(maxDepth(root->left), maxDepth(root->right)) + 1;
    }
};
```
```
执行用时：4 ms, 在所有 C++ 提交中击败了99.22%的用户
内存消耗：17 MB, 在所有 C++ 提交中击败了14.44%的用户
```
