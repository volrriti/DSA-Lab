# Infix to Postfix Conversion

## Algorithm

---
## Program:

```cpp
#include<iostream>  
using namespace std;  
  
#define SIZE 100  
  
class Stack {  
    int top = -1;  
    char stack[SIZE];  
public:  
    Stack() {}  
    void push(int data) {  
        if (top == SIZE - 1) {  
            cout << "Stack Overflow" << endl;  
        }else{  
            stack[++top] = data;  
        }  
    }  
    void pop() {  
        if (top == -1) {  
            cout << "Stack Underflow" << endl;  
        }else {  
            top--;  
        }  
    }  
  
    void display() {  
        if (top == -1) {  
            cout << "Empty Stack" << endl;  
        }else {  
            for (int i = 0; i <=top; i++) {  
                cout << stack[i] << " ";  
            }  
        }  
    }  
  
    int topElement() {  
        if (top == -1) return NULL;  
        return stack[top];  
    }  
};  
  
int precedence(char ch) {  
    if (ch == '$') return 3;  
    if (ch == '*' || ch == '/') return 2;  
    if (ch == '+' || ch == '-') return 1;  
    if (ch == '\0') return -1;  
    return 0;  
}  
  
int main() {  
    Stack postfixStack, operatorStack;  
    char infixString[SIZE];  
    cout << "Enter Infix Expression: ";  
    cin >> infixString;  
    for (int i = 0; infixString[i] != '\0'; i++) {  
        if (isalnum(infixString[i]) == true) {  
            postfixStack.push(infixString[i]);  
        }  
        else {  
  
            // for parenthesis  
            if (infixString[i] == '(') operatorStack.push(infixString[i]);  
            else if (infixString[i] == ')') {  
                while (operatorStack.topElement() != '(') {  
                    postfixStack.push(operatorStack.topElement());  
                    operatorStack.pop();  
                }  
                operatorStack.pop();  
            }  
            else{  
                //precedence  
                while( operatorStack.topElement() != NULL && operatorStack.topElement() != '(' && precedence(operatorStack.topElement()) >= precedence(infixString[i]) ) {  
                    postfixStack.push(operatorStack.topElement());  
                    operatorStack.pop();  
                }  
                operatorStack.push(infixString[i]);  
            }  
        }  
    }  
    while (operatorStack.topElement() != '\0') {  
        postfixStack.push(operatorStack.topElement());  
        operatorStack.pop();  
    }  
  
    cout<<"Postfix Expression: ";  
    postfixStack.display();  
}
```

---

## Output:

```
Enter Infix Expression:A+B*C+(D*E+F)*G

Postfix Expression: A B C * + D E * F + G * +
Process finished with exit code 0
```
