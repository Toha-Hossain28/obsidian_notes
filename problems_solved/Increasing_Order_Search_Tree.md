https://leetcode.com/problems/increasing-order-search-tree/

Given the `root` of a binary search tree, rearrange the tree in **in-order** so that the leftmost node in the tree is now the root of the tree, and every node has no left child and only one right child.

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
    void inOrderTraverse(TreeNode* root, vector<int> &v){
        if(!root){
            return;
        }
        inOrderTraverse(root->left,v);
        v.push_back(root->val);
        inOrderTraverse(root->right,v);
    }
    TreeNode* increasingBST(TreeNode* root) {
        vector<int>v;
        inOrderTraverse(root,v);
        TreeNode* ROOT = new TreeNode(v[0],nullptr,nullptr);
        TreeNode* p = ROOT;
        for(int i=1;i<v.size();i++){
            TreeNode* a = new TreeNode(v[i]);
            p->right = a;
            p = p->right;
        }
        return ROOT;
    }
};
```
