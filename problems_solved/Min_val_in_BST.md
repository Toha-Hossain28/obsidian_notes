```c++
/*
 * class Node
 * {
 * public:
 *     int data;
 *     Node *left;
 *     Node *right;
 *     Node() : data(0), left(nullptr), right(nullptr){};
 *     Node(int x) : data(x), left(nullptr), right(nullptr) {}
 *     Node(int x, Node *left, Node *right) : data(x), left(left), right(right) {}
 * };
 */
int minVal(Node* root){
	// Write your code here.	
	Node* p = root;
	if(root==nullptr){
		return -1;
	}
	while(p){
		if(p->left==nullptr){
			return p->data;
		}
		p = p->left;
		
	}
}
```