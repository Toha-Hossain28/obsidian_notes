
# C Standard

### contains only     `+`, `-`,`*`,`/`

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
			cout<< p->Val;
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
	Stack inTOpost;
	string s;
	cin>>s;
	char arr[s.length()+1];
	int sl=0;
	int i=0;
	while(s[i] != '\0'){
		if(s[i] == '+' || s[i] == '-' || s[i] == '*' || s[i] == '/'){
			if(inTOpost.IsEmpty()){
				inTOpost.Push(s[i]);
				i++;
			}
			else if(s[i] == '+' || s[i] == '-'){
				arr[sl++] = inTOpost.Pop();
			}
			else if(s[i] == '*' || s[i] == '/'){
				if(inTOpost.StackTop() == '+' || inTOpost.StackTop() == '-'){
					inTOpost.Push(s[i]);
					i++;
				}
				else{
					arr[sl++] = inTOpost.Pop();
				}
			}
		}
		else{
			arr[sl++] = s[i];
			i++;
		}
	}
	while(!inTOpost.IsEmpty()){
		arr[sl++] = inTOpost.Pop();
	}
	arr[sl] = '\0';
	cout<<arr<<endl;
}
```

### Contains     `+`,`-`,`*`,`/`,`^`,`()`

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
			cout<< p->Val;
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
			//cout<<"Empty stack"<<endl;
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

bool isOp(char x){
	if(x == '+' || x == '-' || x == '*' || x == '/' || x == '^' || x == '(' || x == ')'){
		return false;
	}
	else{
		return true;
	}
}

int ospre(char x){
	if( x == '+' || x == '-'){
		return 1;
	}
	else if( x == '*' || x == '/'){
		return 3;
	}
	else if (x == '^'){
		return 6;
	}
	else if(x == '('){
		return 7;
	}
	return 0;
}

int ispre(char x){
	if( x == '+' || x == '-'){
		return 2;
	}
	else if( x == '*' || x == '/'){
		return 4;
	}
	else if (x == '^'){
		return 5;
	}
	else if(x == '('){
		return 0;
	}
	return -1;
}

int main(){
	Stack inTOpost;
	string s;
	cin>>s;
	char arr[s.length()+1];
	int i=0;
	int la=0;
	while(s[i] != '\0'){
		if(isOp(s[i])){
			arr[la++] = s[i++];
		}
		else{
			if(ispre(s[i])>=ispre(inTOpost.StackTop())){
				inTOpost.Push(s[i++]);
			}
			else{
				if(inTOpost.StackTop()=='(' || inTOpost.StackTop()==')'){
					inTOpost.Pop();
					continue;
				}
				else{
					arr[la++] = inTOpost.Pop();
				}
			}
		}
	}
	while(!inTOpost.IsEmpty()){
		if(inTOpost.StackTop()=='(' || inTOpost.StackTop()==')'){
			inTOpost.Pop();
			continue;
		}
		else{
			arr[la++] = inTOpost.Pop();
		}
	}
	arr[la] = '\0';
	cout<<arr<<endl;
	return 0;
}
```

Back to [[STACK]]
