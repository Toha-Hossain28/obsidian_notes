```c++
#include <iostream>
#include <stack>
#include <string>

// Function to check if a character is an operator
bool isOperator(char c) {
    return (c == '+' || c == '-' || c == '*' || c == '/' || c == '%' || c == '&' || c == '|' || c == '^');
}

// Function to get the precedence of an operator
int getPrecedence(char c) {
    if (c == '+' || c == '-')
        return 1;
    else if (c == '*' || c == '/' || c == '%')
        return 2;
    else if (c == '&' || c == '|')
        return 3;
    else if (c == '^')
        return 4;
    else
        return 0;
}

// Function to convert infix expression to postfix
std::string infixToPostfix(const std::string& infix) {
    std::string postfix;
    std::stack<char> stack;

    for (char c : infix) {
        if (isalnum(c)) {
            postfix += c;
        } else if (c == '(') {
            stack.push(c);
        } else if (c == ')') {
            while (!stack.empty() && stack.top() != '(') {
                postfix += stack.top();
                stack.pop();
            }
            stack.pop(); // Pop '(' from the stack
        } else if (isOperator(c)) {
            while (!stack.empty() && getPrecedence(c) <= getPrecedence(stack.top())) {
                postfix += stack.top();
                stack.pop();
            }
            stack.push(c);
        }
    }

    while (!stack.empty()) {
        postfix += stack.top();
        stack.pop();
    }

    return postfix;
}

//*******************************************************************************************
// Function to evaluate postfix expression
int evaluatePostfix(const std::string& postfix) {
    std::stack<int> stack;

    for (char c : postfix) {
        if (isdigit(c)) {
            stack.push(c - '0');
        } else if (isOperator(c)) {
            int operand2 = stack.top();
            stack.pop();
            int operand1 = stack.top();
            stack.pop();

            int result;
            switch (c) {
                case '+':
                    result = operand1 + operand2;
                    break;
                case '-':
                    result = operand1 - operand2;
                    break;
                case '*':
                    result = operand1 * operand2;
                    break;
                case '/':
                    result = operand1 / operand2;
                    break;
                case '%':
                    result = operand1 % operand2;
                    break;
                case '&':
                    result = operand1 & operand2;
                    break;
                case '|':
                    result = operand1 | operand2;
                    break;
                case '^':
                    result = operand1 ^ operand2;
                    break;
            }

            stack.push(result);
        }
    }

    return stack.top();
}
/******************************************************************************************/
/******************************************************************************************/
// Function to convert postfix expression to infix
std::string postfixToInfix(const std::string& postfix) {
    std::stack<std::string> stack;

    for (char c : postfix) {
        if (isalnum(c)) {
            std::string operand(1, c);
            stack.push(operand);
        } else if (isOperator(c)) {
            std::string operand2 = stack.top();
            stack.pop();
            std::string operand1 = stack.top();
            stack.pop();

            std::string expression = "(" + operand1 + " " + c + " " + operand2 + ")";
            stack.push(expression);
        }
    }

    return stack.top();
}

int main() {
    std::string infixExpression;
    std::cout << "Enter the infix expression: ";
    std::getline(std::cin, infixExpression);

    std::string postfixExpression = infixToPostfix(infixExpression);
    std::cout << "Postfix expression: " << postfixExpression << std::endl;

    std::string infixFromPostfix = postfixToInfix(postfixExpression);
    std::cout << "Infix expression from postfix: " << infixFromPostfix << std::endl;

    return 0;
}

```
