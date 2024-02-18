#DSA 
```c++
/// here i scanf from the left to right

////if i find any operand then push it into the stack

///if i find any operator i should find the immmediate two operand 

/// (second popped element operator  hobe first  popped element) (this is the tricky part of this evalutaion)

//then push the above evaluting expressinon in the stack

// finally return the top of the stack; 


#include<bits/stdc++.h>
using namespace std;

bool isOperand(char c)
{
    return isdigit(c);
}

double evaluatePostfix(string s)
{
    stack<double>st;
    for(int i=0;s[i]!='\0';i++)
    {
        if(isOperand(s[i]))
        {
            st.push(s[i]-'0');
        }
        else{
            double op2=st.top();
            st.pop();
            double op1=st.top();
            st.pop();

            switch(s[i])
            {
                case '+':
                    st.push(op1 + op2);
                    break;
                case '-':
                    st.push(op1 - op2);
                    break;
                case '*':
                    st.push(op1 * op2);
                    break;
                case '/':
                    st.push(op1 / op2);
                    break;
            }
        }
    }

    return st.top();
}

int main()
{
    string s;
    cin>>s;

    cout<<evaluatePostfix(s)<<endl;
    return 0;
}
```


## ashesh
```c++
#include<iostream>

using namespace std;

  

struct Stack{

    int top;

    int size;

    char* array;

  

    Stack(int n){

        top=-1;

        size=n;

        array=new char[size];

    }

};

  

bool isFull(Stack* st){

    return st->top==st->size-1;

}

  

bool isEmpty(Stack* st){

    return st->top==-1;

}

void push(Stack* st,int item){

    if(isFull(st)){

        return;

    }

    else{

        st->array[++st->top]=item;

    }

}

  

char pop(Stack* st){

    if(isEmpty(st)){

        return -1;

    }

    else{

        int item=st->array[st->top];

        st->top--;

        return item;

    }

}

  

int is_operator(char symbol) {  

    if (symbol == '+' || symbol == '-' || symbol == '*' || symbol == '/') {  

        return 1;  

    }  

    return 0;  

}

int evaluate(Stack* st,string str){

  

    int i=0;

    char ch = str[i];

    int op1,op2,res;

  

    while(ch!='\0'){

        if(ch>='0' && ch<='9'){

            int num=ch-'0';

            push(st,num);

        }

        else if(is_operator(ch)){

            op2=pop(st);

            op1=pop(st);

            switch(ch){

                case '+':res=op1+op2;break;

                        //break;

                case '-':res=op1-op2;break;

                        //break;

                case '*':res=op1*op2;break;

                        //break;

                case '/':res=op1/op2;break;

                        //break;

            }

            push(st,res);

        }

        i++;

        ch=str[i];

    }

    res=pop(st);

    return res;

}

  

int main(){

    string str;

    cin>>str;

  

    Stack* st = new Stack(str.size());

  

    int result = evaluate(st,str);

    cout<<result<<"\n";

    return 0;

}
```