#DSA 
## Max element
```c++
int Max(struct Node* Head){
	struct Node* p= head;
	int x = INT_MIN;
	while(p){
		if(p->data>x){
			x = p->data;
		}
		p = p->next;
	}
	return x; 
}
```

## Recursive Max
```c++
int Rmax(struct Node *Head){
	int x = 0;
	if(p == NULL){
		return INT_MIN;
	}
	else{
		x = Rmax(p->next);
		return x>p->data?x:p->data;
	}
}
```

## Min element
```c++
int Min(struct Node* head) { 
	struct Node* p = head; 
	int x = INT_MAX;
	while (p) { 
		if (p->data < x) { 
			x = p->data; 
		}
		p = p->next; 
	} 
	return x;
 }
```


## Recursive Min element
```c++
int Rmin(struct Node* p) {
    int x;
    if (p == NULL) {
        return INT_MAX;
    } else {
        x = Rmin(p->next);
        return x < p->data ? x : p->data;
    }
}
```
