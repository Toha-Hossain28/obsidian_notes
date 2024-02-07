![STACK](/IMGS/Stack-Data-Structure.png)



- ##  What is **Stack**?

	- ***Stack*** is a linear data structure that follows a particular order in which the operations are performed. The order may be ***LIFO(Last In First Out)*** or ***FILO(First In Last Out)***. ***LIFO***implies that the element that is inserted last, comes out first and ***FILO*** implies that the element that is inserted first, comes out last.



- ## **Stack** Structure
	with [[LINKED_LIST| Linked list]]
	
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
	- Using [Array](Array_Stack_Implementation)
	- Using [Linked List](Linked_List_Stack_Implementatio)
		- [LINKED_LIST](LINKED_LIST)


- ## Problems with **Stack**
	1. [Parenthesis matching](Parenthesis_Matching_using_Stack)
	2. [Infix to Post-fix](Infix_to_Postfix_using_Stack)
	3.  [Post-Fix_Evaluation](Post-Fix_Evaluation)
	4. 