#DSA 
## C Standard
```c++
#include<iostream>
using namespace std;


struct Queue{
	int Size;
	int Front=-1;
	int Rear=-1;
	int *Q;
	
	bool IsEmpty(){
		if(Rear == Front){
			return true;
		}
		else{
			return false;
		}
	}

	bool IsFull(){
		if((Rear+1)%Size == Front){
			return true;
		}
		else{
			return false;
		}
	}

	void Enqueue(int x){
		if(IsFull()){
			cout<<"Queue is full"<<endl;
		}
		else{
			Rear = (Rear + 1) % Size;
			Q[Rear] = x;
		}
	}

	int Dequeue(){
		int x = -1;
		if(IsEmpty()){
			cout<<"Queue is empty"<<endl;
		}
		else{
			Front = (Front + 1) % Size;
			x = Q[Front];
		}
		return x;
	}

	void PrintQ(){
		if (IsEmpty()) {
			cout<< "Queue is empty" << endl;
			return;
		}
		int x = Front+1;
		int y = Rear;
		for(x;x<=y;x++){
			cout<<Q[x]<<" ";
		}
		cout<<endl;
	}
};

  

int main(){

	Queue q;
	q.Size = 6;
	q.Q = new int[q.Size];
	q.Enqueue(1);
	q.Enqueue(2);
	q.Enqueue(3);
	q.Enqueue(4);
	q.Enqueue(5);
	q.PrintQ();
	cout<<q.Dequeue()<<endl;
	q.Enqueue(6);
	q.Enqueue(7);
	cout<<q.Dequeue()<<endl;
	cout<<q.Dequeue()<<endl;
	cout<<q.Dequeue()<<endl;
	cout<<q.Dequeue()<<endl;
	cout<<q.Dequeue()<<endl;
	q.Dequeue();
	return 0;
}
```
