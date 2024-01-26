## C standard(struct) 
```c++
#include<iostream>

using namespace std;

  

struct CLL {

	struct Node {
		
		Node* Prev;
		
		Node* Next;
		
		int val;
		
	};
	
	Node* Head = nullptr;
	
	Node* Tail = nullptr;
	
	  
	
	void InsertFirst(int x) {
		
		Node* a = new Node;
		
		a->Prev = nullptr;
		
		a->Next = nullptr;
		
		a->val = x;
		
		if (Head==nullptr) {
			
			Head = a;
			
			Tail = a;
		
		} 
		
		else {
			
			a->Next = Head;
			
			a->Prev = Tail;
			
			Head->Prev = a;
			
			Tail->Next = Head;
			
			Head = a;
			
		}
	
	}
	
	  
	
	void InsertLast(int x) {
		
		Node* a = new Node;
		
		a->Prev = nullptr;
		
		a->Next = nullptr;
		
		a->val = x;
		
		if (Head == nullptr) {
			
			Head = a;
			
			Tail = a;
			
		} 
		
		else if (Head == Tail) {
			
			Head->Next = a;
			
			Head->Prev = a;
			
			a->Prev = Head;
			
			a->Next = Head;
			
			Tail = a;
			
		} 
		
		else {
			
			Tail->Next = a;
			
			Head->Prev = a;
			
			a->Next = Head;
			
			a->Prev = Tail;
			
			Tail = a;
			
		}
		
	}
	
	  
	
	void PrintLL() {
		
		Node* p = Head;
		
		while(p != nullptr){
			
			cout<<p->val<<" ";
			
			if(p==Tail){
			
			break;
			
			}
			
			else{
				
				p = p->Next;
				
			}
			
		}
		
		cout<<endl;
		
	}
	
	  
	
	void PrintLLRev() {
		
		Node* p = Tail;
		
		while(p != nullptr){
			
			cout<<p->val<<" ";
			
			if(p==Head){
				
				break;
				
			}
			
			else{
				
				p = p->Prev;
				
			}
			
		}
		
		cout << endl;
		
	}
};

  

int main() {

CLL myll;

myll.InsertFirst(1);

myll.PrintLL();

myll.InsertFirst(2);

myll.PrintLL();

myll.InsertLast(3);

myll.PrintLL();

myll.PrintLLRev();

return 0;

}
```
