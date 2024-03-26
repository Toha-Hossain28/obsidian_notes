```c++
#include <iostream>
#include <vector>

using namespace std;

// Definition for a binary tree node
struct TreeNode {
    int val;
    TreeNode *left;
    TreeNode *right;
    TreeNode(int x) : val(x), left(NULL), right(NULL) {}
};

class BinaryTree {
public:
    TreeNode* createBinaryTree(vector<int>& nums) {
        return createBinaryTreeHelper(nums, 0);
    }

private:
    TreeNode* createBinaryTreeHelper(vector<int>& nums, int index) {
        // Base case: if index exceeds the array size or the value at index is -1 (indicating null node)
        if (index >= nums.size() || nums[index] == -1) {
            return nullptr;
        }

        // Create a new node with the value at the current index
        TreeNode* node = new TreeNode(nums[index]);

        // Recursively create left and right subtrees
        node->left = createBinaryTreeHelper(nums, 2 * index + 1);
        node->right = createBinaryTreeHelper(nums, 2 * index + 2);

        return node;
    }
};

// Function to print the inorder traversal of a binary tree
void inorderTraversal(TreeNode* root) {
    if (root) {
        inorderTraversal(root->left);
        cout << root->val << " ";
        inorderTraversal(root->right);
    }
}
// Function to print the preorder traversal of a binary tree
void preorderTraversal(TreeNode* root) {
    if (root) {
        cout << root->val << " ";
        preorderTraversal(root->left);
        preorderTraversal(root->right);
    }
}
// Function to print the postorder traversal of a binary tree
void postorderTraversal(TreeNode* root) {
    if (root) {
        postorderTraversal(root->left);
        postorderTraversal(root->right);
        cout << root->val << " ";
    }
}

int main() {
    vector<int> nums = {1, 2, 3, 4, 5, 6, 7}; // Example array representing the binary tree

    BinaryTree binaryTree;
    TreeNode* root = binaryTree.createBinaryTree(nums);

    cout << "Inorder traversal of the binary tree: ";
    inorderTraversal(root);
    cout << endl;
    cout << "Preorder traversal of the binary tree: ";
    preorderTraversal(root);
    cout << endl;
    cout << "Postorder traversal of the binary tree: ";
    postorderTraversal(root);
    cout << endl;

    return 0;
}

```