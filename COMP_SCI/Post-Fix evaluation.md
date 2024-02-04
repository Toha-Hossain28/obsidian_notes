
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