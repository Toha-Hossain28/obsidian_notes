
https://leetcode.com/problems/range-sum-of-bst/

Given the `root` node of a binary search tree and two integers `low` and `high`, return _the sum of values of all nodes with a value in the **inclusive** range_ `[low, high]`.

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
    int rangeSumBST(TreeNode* root, int low, int high) {
        int sum = 0;
        if(root){
            if(root->val >= low && root->val<=high){
                sum = sum + root->val;
            }
            sum = sum + rangeSumBST(root->left,low,high);
            sum = sum + rangeSumBST(root->right,low,high);
        }
        return sum;
    }
};
```
