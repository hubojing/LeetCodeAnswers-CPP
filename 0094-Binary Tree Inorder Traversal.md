难度： Medium
中序遍历，即左-根-右。这个结构天然递归嘛。
```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    vector<int> vec;
    vector<int> inorderTraversal(TreeNode* root) {
        if(root == nullptr)
        {
            return vec;
        }
        inorderTraversal(root->left);
        vec.push_back(root->val);
        inorderTraversal(root->right);
        return vec;
    }
};
```
```
执行用时：
4 ms, 在所有 C++ 提交中击败了47.90%的用户
内存消耗：10.2 MB, 在所有 C++ 提交中击败了5.00%的用户
```
