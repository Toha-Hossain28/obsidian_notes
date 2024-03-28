Given the root of a binary search tree and an integer k, return true if there exist two elements in the BST such that their sum is equal to k, or false otherwise.

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
    void treeToVector(TreeNode* root,vector<int>&V){
        // TreeNode* p = root;
        if(root==nullptr){
            return;
        }
        treeToVector(root->left,V);
        V.push_back(root->val);
        treeToVector(root->right,V);
    }
    bool binSearch(vector<int> v, int start, int end, int key){
        while(start<=end){
            int mid = (start+end)/2;
            if(v[mid]==key){
                return true;
            }
            else if(v[mid]<key){
                start = mid +1;
            }
            else {
                end = mid -1;
            }
        }
        return false;
    }
    bool findTarget(TreeNode* root, int k) {
        vector<int> V;
        treeToVector(root,V);
        bool ans = false;
        for(int i=0;i<V.size();i++){
            if(binSearch(V,i+1,V.size()-1,k-V[i])){
                ans = true;
                break;
            }
        }
        return ans;
    }
};
```