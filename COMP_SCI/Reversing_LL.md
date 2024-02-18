#DSA 
## Using an ARRAY

```c++
void Reverse1(struct Node *p) {
	int *A,i=0;
	struct Node *q=p; 
	A=(int *)malloc(sizeof(int)*count(p));
	while(q!=NULL) { 
		A[i]=q->data; 
		q=q->next; i++; 
	} 
	q=p; 
	i--; 
	while(q!=NULL) { 
		q->data=A[i]; 
		q=q->next; 
		i--;
	 }
 }
```
## Reversing the link(sliding pointers)

```c++
void Reverse2(struct Node *p) { 
	struct Node *q=NULL,*r=NULL; 
	while(p!=NULL) { 
		r=q; 
		q=p; 
		p=p->next; 
		q->next=r;
	 }
	  first=q; 
}
```

## Using recursion

```c++
void Reverse3(struct Node *q,struct Node *p) {
if(p) {
	Reverse3(p,p->next); 
	p->next=q; 
	} 
	else first=q;
 }
```
