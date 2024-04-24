Given the `root` of a Binary Search Tree (BST), return _the minimum difference between the values of any two different nodes in the tree.

```c++
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left),
 * right(right) {}
 * };
 */
class Solution {
public:
    void treeToVector(TreeNode* root, vector<int>& V) {
        // TreeNode* p = root;
        if (root == nullptr) {
            return;
        }
        treeToVector(root->left, V);
        V.push_back(root->val);
        treeToVector(root->right, V);
    }
    int minDiffInBST(TreeNode* root) {
        vector<int> v;
        treeToVector(root,v);
        int min= INT_MAX;
        for(int i=0;i<v.size()-1;i++){
            for(int j=i+1;j<v.size();j++){
                if(abs(v[i]-v[j])<min){
                    min = abs(v[i]-v[j]);
                }
            }
        }
        return min;
    }
};
```