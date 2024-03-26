```c++
#include <iostream>
using namespace std;

// Node structure for the BST
struct Node {
    int data;
    Node* left;
    Node* right;
    
    Node(int val) : data(val), left(nullptr), right(nullptr) {}
};

// Function to insert a new node into the BST
Node* insert(Node* root, int val) {
    if (root == nullptr) {
        return new Node(val);
    }
    if (val < root->data) {
        root->left = insert(root->left, val);
    } else {
        root->right = insert(root->right, val);
    }
    return root;
}

// In-order traversal of the BST (left-root-right)
void inorderTraversal(Node* root) {
    if (root == nullptr) return;
    inorderTraversal(root->left);
    cout << root->data << " ";
    inorderTraversal(root->right);
}

// Pre-order traversal of the BST (root-left-right)
void preorderTraversal(Node* root) {
    if (root == nullptr) return;
    cout << root->data << " ";
    preorderTraversal(root->left);
    preorderTraversal(root->right);
}

// Post-order traversal of the BST (left-right-root)
void postorderTraversal(Node* root) {
    if (root == nullptr) return;
    postorderTraversal(root->left);
    postorderTraversal(root->right);
    cout << root->data << " ";
}

// Function to delete a node from the BST
Node* deleteNode(Node* root, int key) {
    if (root == nullptr) return root;
    
    if (key < root->data) {
        root->left = deleteNode(root->left, key);
    } else if (key > root->data) {
        root->right = deleteNode(root->right, key);
    } else {
        if (root->left == nullptr) {
            Node* temp = root->right;
            delete root;
            return temp;
        } else if (root->right == nullptr) {
            Node* temp = root->left;
            delete root;
            return temp;
        }
        
        Node* temp = root->right;
        while (temp->left != nullptr) {
            temp = temp->left;
        }
        
        root->data = temp->data;
        root->right = deleteNode(root->right, temp->data);
    }
    return root;
}

int main() {
    // Creating a binary search tree
    Node* root = nullptr;
    int elements[] = {10, 5, 15, 2, 7, 12, 20};
    for (int element : elements) {
        root = insert(root, element);
    }
    
    // Traversing the BST in-order (should print elements in sorted order)
    cout << "In-order traversal: ";
    inorderTraversal(root);
    cout << endl;
    
    return 0;
}

```