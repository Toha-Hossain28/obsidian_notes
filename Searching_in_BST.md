```c++
/*
    Following is the Binary Tree node structure:

    template <typename T>
    class BinaryTreeNode
    {
    public:
        T data;
        BinaryTreeNode<T> *left, *right;
        BinaryTreeNode() : data(0), left(NULL), right(NULL) {}
        BinaryTreeNode(T x) : data(x), left(NULL), right(NULL) {}
        BinaryTreeNode(T x, BinaryTreeNode<T> *left, BinaryTreeNode<T> *right) : data(x), left(left), right(right) {}
    };

*/

bool searchInBST(BinaryTreeNode<int> *root, int x) {
    // Write your code here.
    while (root) {
        if (root->data == x) {
            return true;  // Value found
        } else if (root->data < x) {
            root = root->right;  // Search in the right subtree
        } else {
            root = root->left;  // Search in the left subtree
        }
    }
    return false;  // Value not found
}
```

### Recursive
```c++
/*
    Following is the Binary Tree node structure:

    template <typename T>
    class BinaryTreeNode
    {
    public:
        T data;
        BinaryTreeNode<T> *left, *right;
        BinaryTreeNode() : data(0), left(NULL), right(NULL) {}
        BinaryTreeNode(T x) : data(x), left(NULL), right(NULL) {}
        BinaryTreeNode(T x, BinaryTreeNode<T> *left, BinaryTreeNode<T> *right) : data(x), left(left), right(right) {}
    };

*/

bool searchInBST(BinaryTreeNode<int> *root, int x) {
    // Write your code here.
    // bool result = false;
    if(root){
        if(root->data==x){
            return true;
        }
        else if(root->data<x){
            return searchInBST(root->right, x);
        }
        else{
            return searchInBST(root->left, x);
        }
    }
    return false;
}
```
