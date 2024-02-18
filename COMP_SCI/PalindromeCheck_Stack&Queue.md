#DSA 

```c++
#include<bits/stdc++.h>
using namespace std;

struct Queue {
    struct Node {
        Node* next;
        char val;
    };
    Node* Front = nullptr;
    Node* Rear = nullptr;


    void Enqueue(char x){
        Node* a = new Node;
        a->next = nullptr;
        a->val = x;
        if(Rear){
            Rear->next = a;
            Rear = a;
        }
        else{
            Front = a;
            Rear = a;
        }
    }

    int Dequeue(){
        if(!Front){
            return '\0';
        }
        if(Front == Rear){
            char x = Front->val;
            Front = nullptr;
            Rear = nullptr;
            return x;
        }
        else{
            char x = Front->val;
            Front = Front->next;
            return x;
        }
    }

    void PrintQ() {
        Node* p = Front;
        while (p) {
            cout << p->val<<" ";
            p = p->next;
        }
        cout<<endl;
    }
};

struct Stack{
    struct Node{
        char Val;
        Node* Next;
    };

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

    char StackTop(){
        if(Top == nullptr){
            cout<<"Empty stack"<<endl;
            return '\0';
        }
        else{
            return Top->Val;
        }
    }

    char Peek(int x){
        if(IsEmpty()){
            cout<<"Empty stack"<<endl;
            return '\0';
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
                return '\0';
            }
        }
    }
};

int main(){
    Stack S;
    Queue Q;
    string s = "abcdcb";
    int len = s.length();
    if(len%2==0){
        int i = 0;
        while(i<len/2){
            S.Push(s[i]);
            i++;
        }
        while(i<len){
            Q.Enqueue(s[i]);
            i++;
        }
    }
    else{
        int i = 0;
        while(i<len/2){
            S.Push(s[i]);
            i++;
        }
        i++;
        while(i<len){
            Q.Enqueue(s[i]);
            i++;
        }
    }
    while(!S.IsEmpty()){
        char x = S.Pop();
        char y = Q.Dequeue();
        if(x!=y){
            cout<<"Not palindrome"<<endl;
            return 0;
        }
    }
    cout<<"Palindrome"<<endl;
    return 0;
}

```