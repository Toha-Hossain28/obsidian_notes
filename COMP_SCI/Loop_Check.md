## Check if the LL is linear or not?

### 2 pointer method (==if the LL don't have Tail pointer==)

```c++
bool isloop(){
	Node* p,q;
	p=q=Head;
	do{
		p = p->next;
		q = q->next;
		if(q != nullptr){
			q = q->next;
		}
	}while(p && q && p!=q);
	if(p==q){
		return true;
	}
	else{
		return false;
	}
}
```
