# Postfix Evaluation 
## Algorithm
1. Stack is Implemented as in [[01-Stack-Implementation-using-Array]]
2. `resultStack` is created
3. Read Postfix Expression `postfixString`
4. Loop `postfixString` until `'/0'`:
	1. `ch` is a character of `postfixString`
	2. If `ch` is a digit, push it to `resultStack`
	3. If `ch` is an operator, operate on last two elements of `resultStack` in `result`
	4. Pop last two elements and then push `result` to `resultStack`
5. Display the remaining element of `resultStack`


## Program
```cpp
#include<iostream>  
#include<cmath>  
using namespace std;  
  
#define SIZE 100  
  
class Stack {  
    int top = -1;  
    int stack[SIZE];  
    public:  
        Stack() {}  
  
        void push(int data) {  
            if (top == SIZE - 1) {  
                cout << "Stack Overflow" << endl;  
            } else {  
                stack[++top] = data;  
            }  
        }  
  
        void pop() {  
            if (top == -1) {  
                cout << "Stack Underflow" << endl;  
            } else {  
                top--;  
            }  
        }  
  
        int topElement() {  
            if (top == -1) return INT_MIN;  
            return stack[top];  
        }  
  
        void display() {  
            if (top == -1) {  
                cout << "Empty Stack" << endl;  
            } else {  
                for (int i = top; i >= 0; i--) {  
                    cout << stack[i] << " ";  
                }  
                cout << endl;  
            }  
        }  
};  
  
int main() {  
    Stack resultStack;  
    char postfixString[SIZE];  
    cout << "Enter Postfix Expression: ";  
    cin >> postfixString;  
  
    for (int i = 0; postfixString[i] != '\0'; i++) {  
        char ch = postfixString[i];  
  
        if (isdigit(ch)) {  
            resultStack.push(ch - '0');   // convert char digit to int  
            // '0' is ASCII code of 0. So for eg. (6 - '0')->(54-48) = 6        } else {  
            int b = resultStack.topElement(); resultStack.pop();  
            int a = resultStack.topElement(); resultStack.pop();  
  
            int result;  
            if      (ch == '+') result = a + b;  
            else if (ch == '-') result = a - b;  
            else if (ch == '*') result = a * b;  
            else if (ch == '/') result = a / b;  
            else if (ch == '$') result = pow(a, b);  
  
            resultStack.push(result);  
        }  
    }  
  
    cout << "Result: " << resultStack.topElement() << endl;  
}
```

## Output

```
Enter Postfix Expression:123*+45*6+7*+ 

Result: 189

Process finished with exit code 0
```