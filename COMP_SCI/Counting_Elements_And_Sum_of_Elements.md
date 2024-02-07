## A function to count the number of elements in a LL
```c++
int elementCount(struct Node *head){
	struct Node* p = head;
	int count = 0;
		while(p != NULL){
			count++;
			p = p->next;
		}
}
```

## Recursive
```c++
int elementCount(struct Node *head){
	if(p== NULL){
		return 0;
	}
	else{
		return elementCount(head->next)+1;
	}
}
```

## Sum of elements
```c++
int sum(struct Node* head){
	struct Node* p = head;
	int sum = 0;
	while(p!=NULL){
		sum = sum + p->data;
		p = p->next;
	}
	return sum;
}
```

## Recursive Sum of elements 
```c++
int sum(struct Node* head){
	struct Node *p = head;
	if(p==NULL){
		return 0;
	}
	else{
		return sum(p->next)+ p->data;
	}
}
```
