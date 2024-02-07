## C standard (Struct)
```c++
#include <iostream>
using namespace std;

struct LL {
	struct Node {
		Node* next;
		int val;
	};
	Node* Head = nullptr;
	Node* Tail = nullptr;
		
		
	void InsertFirst(int x) {
		Node* a = new Node;
		a->next = nullptr;
		a->val = x;
		if (Head == nullptr) {
			Head = a;
			Tail = a;
		} 
		else {
			a->next = Head;
			Head = a;
		}
	}
		
		
	void InsertLast(int x){
		Node* a = new Node;
		a->next = nullptr;
		a->val = x;
		if(Tail){
			Tail->next = a;
			Tail = a;
		}
		else{
			Head = a;
			Tail = a;
		}
	}
		
		
	int DelFirst(){
		if(!Head){
		return -1;
		}
		if(Head == Tail){
			int x = Head->val;
			Head = nullptr;
			Tail = nullptr;
			return x;
		}
		else{
			int x = Head->val;
			Head = Head->next;
			return x;
		}
	}
		
		
	int DelLast(){
		if(!Head){
			return -1;
		}
		else if(Head == Tail){
			int x = Head->val;
			Head = nullptr;
			Tail = nullptr;
			return x;
		}
		else{
			Node* p = Head;
			while (p->next != Tail) {
				p = p->next;
			}
			int x = Tail->val;
			p->next = nullptr;
			Tail = p;
			return x;
		}
	}
		
		
	void PrintLL() {
		Node* p = Head;
		while (p) {
			cout << p->val << endl;
			p = p->next;
		}
	}
};

int main() {

	LL myll;
	
	myll.InsertFirst(1);
	
	myll.InsertFirst(2);
	
	myll.InsertFirst(3);
	
	myll.InsertLast(4);
	
	myll.PrintLL();
	
	cout<<myll.DelLast()<<endl;
	
	myll.PrintLL();
	
	return 0;
}
```
