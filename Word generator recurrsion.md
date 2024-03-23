```c++
#include<bits/stdc++.h>
using namespace std;

struct Stack{
    struct Node{
        char Val;
        Node* Next;
    };

    int length = 0;
    Node* Top = nullptr;

    void Push(char x){
        Node* a = new Node;
        a->Next = nullptr;
        if(a == nullptr){
            cout<<"Stack Overflow"<<endl;
        }
        else{
            a->Val = x;
            a->Next = Top;
            Top = a;
            length++;
        }
    }

    char Pop(){
        Node* p;
        char x = '\0';
        if(Top == nullptr){
            cout<<"Stack is empty"<<endl;
        }
        else{
            p = Top;
            x = Top->Val;
            Top = Top->Next;
            delete p;
            length--;
        }
        return x;
    }

    void PrintS(){
        Node* p = Top;
        while(p != nullptr){
            cout<< p->Val <<" ";
            p = p->Next;
        }
        cout<<endl;
    }

    bool IsFull(){
        Node* p = new Node;
        if(p == nullptr){
            return false;
        }
        else{
            delete p;
            return true;
        }
    }

    bool IsEmpty(){
        if(Top == nullptr){
            return true;
        }
        else{
            return false;
        }
    }

    int StackTop(){
        if(Top == nullptr){
            cout<<"Empty stack"<<endl;
            return -1;
        }
        else{
            return Top->Val;
        }
    }

    int Peek(int x){
        if(IsEmpty()){
            cout<<"Empty stack"<<endl;
            return -1;
        }
        else{
            Node* p = Top;
            for(int i=0; p != nullptr && i<x-1; i++){
                p = p->Next;
            }
            if(p != nullptr){
                return p->Val;
            }
            else{
                return -1;
            }
        }
    }
};

Stack copyStack(const Stack& originalStack) {
    Stack copiedStack;
    Stack::Node* temp = originalStack.Top;

    // Traverse the original stack and push its elements into the copied stack
    while (temp != nullptr) {
        copiedStack.Push(temp->Val);
        temp = temp->Next;
    }

    return copiedStack;
}

void generateWords(Stack &s,string voc){
    if(s.length==voc.size()){
        s.PrintS();
        return;
    }
    for (int i = 0; i < voc.size();i++){
        Stack copy_Stack = copyStack(s);
        copy_Stack.Push(voc[i]);
        generateWords(copy_Stack, voc);
    }
}

int main(){
    Stack stq;
    string voc = "abc";
    generateWords(stq, voc);
    return 0;
}
```

```output
a a a 
b a a 
c a a 
a a b 
b a b 
c a b 
a a c 
b a c 
c a c 
a b a 
b b a 
c b a 
a b b 
b b b 
c b b 
a b c 
b b c 
c b c 
a c a 
b c a 
c c a 
a c b 
b c b 
c c b 
a c c 
b c c 
c c c
```
