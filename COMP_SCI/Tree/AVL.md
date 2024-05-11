```c++
#include<bits/stdc++.h>
using namespace std;


struct Node
{
    int data;
    Node *left;
    Node *right;
    int height;
};

//get the height of node
int height( Node *N)
{
    if(N == nullptr)
    {
        return 0;
    }
    return N->height;
}

int max(int a, int b)
{
    return (a > b) ? a : b;
}

//new node creation
Node* newNode(int key)
{
    Node *node = new Node();
    node->data = key;
    node->left = nullptr;
    node->right = nullptr;
    node->height = 1;
    return node;
}

Node *rightRotate(Node *y)
{
    Node *x = y->left;
    Node *T2 = x->right;

    x->right = y;
    y->left = T2;

    y->height = max(height(y->left), height(y->right)) + 1;
    x->height = max(height(x->left), height(x->right)) + 1;

    return x;
}


Node *leftRotate(Node* x)
{
    Node *y = x->right;
    Node *T2 = y->left;

    y->left = x;
    x->right = T2;

    x->height = max(height(x->left), height(x->right)) + 1;
    y->height = max(height(y->left), height(y->right)) + 1;

    return y;
}

int getBalance(Node *N)
{
    if(N == nullptr)
    {
        return 0;
    }
    return height(N->left) - height(N->right);
}


Node* Insert(Node* node, int key)
{
    //normal BST insertion
    if(node == nullptr)
    {
        return (newNode(key));
    }

    if(key < node->data)
    {
        node->left = Insert(node->left, key);
    }

    else if(key > node->data)
    {
        node->right = Insert(node->right, key);
    }
    else{
        return node;
    }

    //update height of this ancestor node
    node->height = 1 + max(height(node->left), height(node->right));

    int balance = getBalance(node);


    //LL
    if(balance > 1 && key < node->left->data)
    {
        return rightRotate(node);
    }

    //RR
    if(balance < -1 && key > node->right->data)
    {
        return leftRotate(node);
    }

    //LR
    if(balance > 1 && key > node->left->data)
    {
        node->left = leftRotate(node->left);
        return rightRotate(node);
    }

    //RL
    if(balance < -1 && key < node->right->data)
    {
        node->right = rightRotate(node->right);
        return leftRotate(node);
    }

    return node;
}

/* Given a non-empty binary search tree, 
return the node with minimum key value 
found in that tree. Note that the entire 
tree does not need to be searched. */
Node * minValueNode(Node* node) 
{ 
    Node* current = node; 
 
    /* loop down to find the leftmost leaf */
    while (current->left != NULL) 
        current = current->left; 
 
    return current; 
}

Node* Delete(Node* root, int key)
{
    if(root == nullptr)
    {
        return root;
    }
    else if(key < root->data)
    {
        root->left = Delete(root->left, key);
    }
    else if( key > root->data)
    {
        root->right = Delete(root->right, key);
    }
    else 
    {
        if(root->left == nullptr || root->right == nullptr)
        {
            Node *temp = root->left ? root->left : root->right;

            if( temp == nullptr)
            {
                temp = root;
                root = nullptr;
            }
            else
            {
                *root = *temp;
            }
            free(temp);
        }
        else
        {
            Node* temp = minValueNode(root->right);
            root->data = temp->data;
            root->right = Delete(root->right, temp->data);
        }
    }

    if(root == nullptr)
    {
        return root;
    }
    
    root->height = 1 + max(height(root->left), height(root->right));

    int balance = getBalance(root);

    if(balance > 1 && getBalance(root->left) >= 0)
    {
        return rightRotate(root);
    }

    if(balance > 1 && getBalance(root->left) < 0)
    {
        root->left = leftRotate(root->left);
        return rightRotate(root);
    }

    if(balance < -1 && getBalance(root->right) <= 0)
    {
        return leftRotate(root);
    }

    if(balance < -1 && getBalance(root->right) > 0)
    {
        root->right = rightRotate(root->right);
        return leftRotate(root);
    }

    return root;
}

void preOrder( Node* root)
{
    if(root != nullptr)
    {
        cout << root->data << " ";
        preOrder(root->left);
        preOrder(root->right);
    }
}


int main()
{
    return 0;
}
```
