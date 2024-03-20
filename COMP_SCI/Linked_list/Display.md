#DSA 
## A function to display a LL
```c++
void Display(struct Node *head){
	struct Node* p = head;
	while( p != NULL ){
		cout<< p->data;
		p = p->next;
	}
}
```

##  A recursive function to print a LL
```c++
void Display(struct Node* head){
struct Node* p = head;
	if(p != NULL){
		cout<< p->date;
		Display(p->next);
	}
}
```
