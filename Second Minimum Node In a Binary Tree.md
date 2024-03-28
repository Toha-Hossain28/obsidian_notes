Given a non-empty special binary tree consisting of nodes with the non-negative value, where each node in this tree has exactly `two` or `zero` sub-node. If the node has two sub-nodes, then this node's value is the smaller value among its two sub-nodes. More formally, the property `root.val = min(root.left.val, root.right.val)` always holds.

Given such a binary tree, you need to output the **second minimum** value in the set made of all the nodes' value in the whole tree.

If no such second minimum value exists, output -1 instead.

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
     void treeToSet(TreeNode* root, set<int>& s) {
        if (root == nullptr) {
            return;
        }
        s.insert(root->val);
        treeToSet(root->left, s);
        treeToSet(root->right, s);
    }
    
    int findSecondMinimumValue(TreeNode* root) {
        set<int> s;
        treeToSet(root, s);
        
        if (s.size() < 2) {
            return -1;
        }
        
        auto it = s.begin();
        advance(it, 1);
        return *it;
    }  
};
```