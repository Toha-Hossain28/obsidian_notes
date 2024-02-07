## If the LL is sorted
```c++
void RemoveDuplicate(struct Node *p) {
	struct Node *q=p->next; 
	while(q!=NULL) { 
		if(p->data!=q->data) {
			p=q; 
			q=q->next; 
		}
		else {
			p->next=q->next;
			free(q);
			q=p->next;
		}
	}
}
```
