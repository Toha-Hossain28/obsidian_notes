#DSA 
## Is the LL sorted?

```c++
int isSorted(struct Node *p) {
	int x=INT_MIN;
	while(p!=NULL) { 
		if(p->data < x) 
			return 0; 
		x=p->data; 
		p=p->next; 
	} 
	return 1;
}
```

