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
	
	int DelFirst(){
		
		if(Head == nullptr){
		
			return -1;
			
		}
		
		else if(Head == Tail){
			
			int x = Head->val;
			
			Head = nullptr;
			
			Tail = nullptr;
			
			return x;
			
		}
		
		else{
			
			int x = Head->val;
			
			Tail->Next = Head->Next;
			
			Head = Head->Next;
			
			Head->Prev = Tail;
			
			return x;
			
		}
		
	}
	
	  
	
	int DelLast(){
		
		if(Head == nullptr){
			
			return -1;
			
		}
		
		else if(Head == Tail){
			
			int x = Head->val;
			
			Head = nullptr;
			
			Tail = nullptr;
			
			return x;
			
		}
		
			else{
			
			int x = Tail->val;
			
			Tail = Tail->Prev;
			
			Tail->Next = Head;
			
			Head->Prev = Tail;
			
			return x;
			
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
