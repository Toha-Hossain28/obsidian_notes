## C standard
```c++
#include<iostream>
using namespace std;

  
struct Queue {
	struct Node {
		Node* next;
		int val;
	};
	Node* Front = nullptr;
	Node* Rear = nullptr;
	
	void Enqueue(int x){
		Node* a = new Node;
		a->next = nullptr;
		a->val = x;
		if(Rear){
			Rear->next = a;
			Rear = a;
		}
		else{
			Front = a;
			Rear = a;
		}
	}
	
	int Dequeue(){
		if(!Front){
			return -1;
		}
		if(Front == Rear){
			int x = Front->val;
			Front = nullptr;
			Rear = nullptr;
			return x;
		}
		else{
			int x = Front->val;
			Front = Front->next;
			return x;
		}
	}
	
	void PrintQ() {
		Node* p = Front;
		while (p) {
			cout << p->val<<" ";
			p = p->next;
		}
		cout<<endl;
	}
};

  

int main(){
	
	Queue myQ;
	myQ.Enqueue(1);
	myQ.Enqueue(2);
	myQ.Enqueue(3);
	myQ.Enqueue(4);
	myQ.Enqueue(5);
	myQ.PrintQ();
	cout<<myQ.Dequeue()<<endl;
	cout<<myQ.Dequeue()<<endl;
	cout<<myQ.Dequeue()<<endl;
	myQ.PrintQ();
	cout<<myQ.Dequeue()<<endl;
	cout<<myQ.Dequeue()<<endl;
	cout<<myQ.Dequeue()<<endl;
	return 0;
}
```
