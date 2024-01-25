## C standard 
```c++
#include<iostream>
using namespace std;

struct DLL{
	struct Node{
		Node* Prev;
		Node* Next;
		int val;
	};
	Node* Head = nullptr;
	Node* Tail = nullptr;
	
	void InsertFirst(int x){
		Node* a = new Node;
		a->Prev = nullptr;
		a->Next = nullptr;
		a->val = x;
		if(!Head){
			Head = a;
			Tail = a;
		}
		else{	
			a->Next = Head;
			Head->Prev = a;
			Head = Head->Prev;
		}
	}
	
	void InsertLast(int x){
		Node* a = new Node;
		a->Prev = nullptr;
		a->Next = nullptr;
		a->val = x;
		if(!Head){
			Head = a;
			Tail = a;
		}
		else{	
			a->Prev = Tail;
			Tail->Next = a;
			Tail = Tail->Next;
		}
	}
	
	int DelFirst(){
		if(!Head){
			return -1;
		}
		else if (Head == Tail){	
			int x = Head->val;
			Head = nullptr;
			Tail = nullptr;
			return x;
		}
		else{	
			int x = Head->val;
			Head = Head->Next;
			Head->Prev = nullptr;
			return x;
		}
	}
	
	int DelLast(){
		if(!Head){
			return -1;
		}
		else if (Head == Tail){
			int x = Head->val;
			Head = nullptr;
			Tail = nullptr;
			return x;
		}
		else{
			int x = Tail->val;
			Tail = Tail->Prev;
			Tail->Next = nullptr;
			return x;
		}
	}
	
	void PrintLL(){
		Node* p = Head;
		while(p){
			cout<<p->val<<" ";
			p = p->Next;
		}
		cout<<endl;
	}
};

  

int main(){
	
	DLL myll;
	
	myll.InsertFirst(1);
	
	myll.InsertFirst(0);
	
	myll.InsertLast(2);
	
	myll.InsertLast(3);
	
	myll.PrintLL();
	
	cout<<myll.DelFirst()<<endl;
	
	cout<<myll.DelLast()<<endl;
	
	myll.PrintLL();
	
	return 0;
}
```
