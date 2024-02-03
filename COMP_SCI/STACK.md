![[Stack-Data-Structure.png]]



- ##  What is **Stack**?

	- ***Stack*** is a linear data structure that follows a particular order in which the operations are performed. The order may be ***LIFO(Last In First Out)*** or ***FILO(First In Last Out)***. ***LIFO***implies that the element that is inserted last, comes out first and ***FILO*** implies that the element that is inserted first, comes out last.



- ## **Stack** Structure
	with [[LINKED LIST | Linked list]]
	
```c++
struct Stack{
	struct Node{
	int Val;
	Node* Next;
	};
	Node* Top = nullptr;
};
```
	
	with array
	
```c++
struct Stack{
	int Size;
	int Top=-1;
	int* S;
};
```



- ## Implementation Of **Stack**
	- Using [[Array Stack Implementation | Array]]
	- Using [[Linked List Stack implementation| Linked List]]
		- [[LINKED LIST]]



- ## Problems with **Stack**
	1. [[Parenthesis Matching using stack | Parenthesis matching]]
	2. [[Infix to Postfix using stack | Infix to Post-fix]]
	3.  [[Post-Fix evaluation]]
	4. 