
https://leetcode.com/problems/search-in-a-binary-search-tree/

You are given the `root` of a binary search tree (BST) and an integer `val`.

Find the node in the BST that the node's value equals `val` and return the sub-tree rooted with that node. If such a node does not exist, return `null`.
```c++
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
    TreeNode* searchBST(TreeNode* root, int val) {
        TreeNode* p = nullptr;
        if (root) {
            if (root->val == val) {
                p = root;
            } else if (root->val > val) {
                p = searchBST(root->left, val);
            } else {
                p = searchBST(root->right, val);
            }
        }
        return p;
    }
};
```