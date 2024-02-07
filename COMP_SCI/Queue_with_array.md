## C standard
```c++
#include<iostream>

using namespace std;

  

struct Queue{
	int Size;
	int Front=-1;
	int Rear=-1;
	int *Q;
	
	void Enqueue(int x){
		if(Rear == Size-1){
			cout<<"Queue is full"<<endl;
		}
		else{
			Q[++Rear] = x;
		}
	}
	
	int Dequeue(){
		int x = -1;
		if(Rear == Front){
			cout<<"Queue is empty"<<endl;
		}
		else{
			x = Q[++Front];
		}
		return x;
	}	  
	
	bool IsEmpty(){
		if(Rear == Front){
			return true;
		}
		else{
			return false;
		}
	}
	
	bool IsFull(){
		if(Rear == Size - 1){
			return true;
		}
		else{
			return false;
		}
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
	Queue myQ;
	cin>>myQ.Size;
	myQ.Q = new int[myQ.Size];
	cout<<myQ.IsEmpty()<<endl;
	myQ.Enqueue(1);
	myQ.Enqueue(2);
	myQ.Enqueue(3);
	cout<<myQ.IsFull()<<endl;
	myQ.Enqueue(4);
	myQ.Enqueue(5);
	myQ.PrintQ();
	cout<<myQ.IsFull()<<endl;
	cout<<myQ.Dequeue()<<endl;
	cout<<myQ.Dequeue()<<endl;
	cout<<myQ.Dequeue()<<endl;
	myQ.PrintQ();
	cout<<myQ.Dequeue()<<endl;
	cout<<myQ.Dequeue()<<endl;

return 0;

}
```