## **C** standard

```c++
#include<iostream>

using namespace std;

struct Stack{
	int Size;
	int Top=-1;
	int* S;
	
	bool IsEmpty(){
		if(Top == -1){
			return true;
		}
		else{
			return false;
		}
	}
	
	bool IsFull(){
		if(Top == Size-1){
			return true;
		}
		else{
			return false;
		}
	}
	
	void Push(int x){
		if(IsFull()){
			cout<<"Stack Overflow"<<endl;
		}
		else{
			Top++;
			S[Top] = x;
		}
	}
	
	int Pop(){
		if(IsEmpty()){
			cout<<"Stack Underflow"<<endl;
			return -1;
		}
		else{
			int x = S[Top];
			S[Top] = 0;
			Top--;
			return x;
		}
	}
	
	int Peek(int x){
		if(IsEmpty()){
			cout<<"Empty Stack"<<endl;
			return -1;
		}
		else{
			if(Top-x+1<0){
				cout<<"Invalid Position"<<endl;
				return -1;
			}
			else{
				return S[Top-x+1];
			}
		}
	}
	
	int StackTop(){
		if(IsEmpty()){
			cout<<"Stack Empty"<<endl;
			return -1;
		}
		else{
			return S[Top];
		}
	}
	
	void PrintS(){
		if(IsEmpty()){
			cout<<"Empty Stack"<<endl;
		}
		else{
			int n = Top;
			while(n>-1){
				cout<<S[n]<<" ";
				n--;
			}
			cout<<endl;
		}
	}
};

  
  

int main(){
  
	Stack mystack;
	
	int n;
	
	cin>>n;
	
	mystack.Size = n;
	
	mystack.S = new int[mystack.Size];
	
	cout<<mystack.IsEmpty()<<endl;
	
	mystack.Push(1);
	
	mystack.StackTop();
	
	mystack.Push(2);
	
	mystack.Push(3);
	
	mystack.Push(4);
	
	mystack.Push(5);
	
	cout<<mystack.IsFull()<<endl;
	
	cout<<mystack.IsEmpty()<<endl;
	
	mystack.PrintS();
	
	cout<<mystack.Pop()<<endl;
	
	mystack.PrintS();
	
	//cout<<mystack.Pop()<<endl;
	
	//mystack.PrintS();
	
	cout<<mystack.Peek(2)<<endl;
	
	cout<<mystack.Peek(5)<<endl;
	
	return 0;
}
```
