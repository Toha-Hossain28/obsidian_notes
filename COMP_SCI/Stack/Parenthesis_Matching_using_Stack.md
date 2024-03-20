#DSA 
## C standard

```c++
#include<iostream>
using namespace std;

struct Stack{
	struct Node{
		char Val;
		Node* Next;
	};
	
	Node* Top = nullptr;
	
	void Push(char x){
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
	
	char Pop(){
		Node* p;
		char x = '\0';
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
	
	char StackTop(){
		if(Top == nullptr){
			cout<<"Empty stack"<<endl;
			return '\0';
		}
		else{
		return Top->Val;
		}
	}
	
	char Peek(int x){
		if(IsEmpty()){
			cout<<"Empty stack"<<endl;
			return '\0';
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
				return '\0';
			}
		}
	}

};

  

int main(){
	string s;
	cin>>s;
	int i=0;
	Stack Pmatching;
	while (s[i]!='\0'){
		if(s[i]=='(' || s[i]== '{' || s[i]=='['){
			Pmatching.Push(s[i]);
		}
		if(s[i]==')'){
			if(Pmatching.IsEmpty()){
				cout<<"Not Matching"<<endl;
				return 0;
				}
			else{
				if(Pmatching.StackTop()=='('){
					Pmatching.Pop();
				}
				else{
					cout<<"Not Matching"<<endl;
				return 0;
				}
			}
		}
		if(s[i]=='}'){
			if(Pmatching.IsEmpty()){
				cout<<"Not Matching"<<endl;
				return 0;
			}
			else{
				if(Pmatching.StackTop()=='{'){
					Pmatching.Pop();
				}
				else{
					cout<<"Not Matching"<<endl;
					return 0;
				}
			}
		}
		if(s[i]=='['){
			if(Pmatching.IsEmpty()){
				cout<<"Not Matching"<<endl;
				return 0;
			}
			else{
				if(Pmatching.StackTop()=='['){
					Pmatching.Pop();
				}
				else{
					cout<<"Not Matching"<<endl;
					return 0;
				}
			}
		}
		i++;
	}
	if(Pmatching.IsEmpty()){
		cout<<"Matching"<<endl;
	}
	else{
		cout<<"Not Matching"<<endl;
	}
return 0;
}
```

Go back to [STACK](STACK.md)
