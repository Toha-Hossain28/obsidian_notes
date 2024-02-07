## C standard
```c++
#include<iostream>
using namespace std;

  

struct Stack{
	struct Node{
		int Val;
		Node* Next;
	};
	
	Node* Top = nullptr;
	
	void Push(int x){
		Node* a = new Node;
		a->Next = nullptr;
		if(a == nullptr){
			cout<<"Stack Overflow"<<endl;
		}
		else{
			a->Val = x;
			a->Next = Top;
			Top = a;	
		}
	}
	
	int Pop(){
		Node* p;
		int x = -1;
		if(Top == nullptr){
			cout<<"Stack is empty"<<endl;
		}
		else{
			p = Top;
			x = Top->Val;
			Top = Top->Next;
			delete p;
		}
		return x;
	}
	
	void PrintS(){
		Node* p = Top;
		while(p != nullptr){
			cout<< p->Val <<" ";
			p = p->Next;
		}
		cout<<endl;
	}
	
	bool IsFull(){
		Node* p = new Node;
		if(p == nullptr){
			return false;
		}
		else{
			delete p;
			return true;
		}
	}
	
	bool IsEmpty(){
		if(Top == nullptr){
			return true;
		}
		else{
			return false;
		}
	}
	
	int StackTop(){
		if(Top == nullptr){
			cout<<"Empty stack"<<endl;
			return -1;
		}
		else{
			return Top->Val;
		}
	}
	
	int Peek(int x){
		if(IsEmpty()){
			cout<<"Empty stack"<<endl;
			return -1;
		}
		else{
			Node* p = Top;
			for(int i=0; p != nullptr && i<x-1; i++){
				p = p->Next;
			}
			if(p != nullptr){
				return p->Val;
			}
			else{
			return -1;
			}
		}
	}
};

  

int main(){
	
	Stack mystack;
	
	cout<<"--------- Empty check ---------"<<endl;
	
	cout<<mystack.IsEmpty()<<endl;
	
	mystack.Push(1);
	
	mystack.Push(2);
	
	mystack.Push(3);
	
	cout<<"--------- End of Push ---------"<<endl;
	
	cout<<"--------- Printing ---------"<<endl;
	
	mystack.PrintS();
	
	cout<<"--------- End of Printing ---------"<<endl;
	
	cout<<"--------- Peeking ---------"<<endl;
	
	cout<<mystack.Peek(1)<<endl;
	
	cout<<mystack.Peek(2)<<endl;
	
	cout<<mystack.Peek(3)<<endl;
	
	cout<<mystack.Peek(4)<<endl;
	
	cout<<"--------- Poping ---------"<<endl;
	
	cout<<mystack.Pop()<<endl;
	
	mystack.PrintS();
	
	cout<<mystack.Pop()<<endl;
	
	mystack.PrintS();
	
	cout<<"--------- Stack Top ---------"<<endl;
	
	cout<<mystack.StackTop<<endl;
	
	return 0;

}
```
