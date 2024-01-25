## Linear Search on LL
```c++
Node* search(struct Node* Head, int key){
	struct Node* p = Head;
	while(p){
		if(p->data == key){
			return p;
		}
		else{
			p = p->next;
		}
	}
	return NULL;
}
```

## Recursive
```c++
Node* search(struct Node* Head, int key){
	struct Node* p = Head;
	if(p == NULL){
		return NULL;
	}
	if(key == p->data){
		return p;
	}
	else{
		return search(p->next,key);
	}
}
```

## Improved search
### Move to head(Don't use transposition on LL)
```c++

```