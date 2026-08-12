# Prefix Evaluation
## Algorithm
1. Stack is Implemented as in [[01-Stack-Implementation-using-Array]]
2. `resultStack` is created
3. Read Postfix Expression `prefixString`
4. Loop `prefixString` in reverse from `strlen(prefixString)':
	1. `ch` is a character of `prefixString`
	2. If `ch` is a digit, push it to `resultStack`
	3. If `ch` is an operator, operate on last two elements **in reverse order** of `resultStack` in `result`
	4. Pop last two elements and then push `result` to `resultStack`
5. Display the remaining element of `resultStack`
## Program
```cpp
#include<iostream>  
#include<cmath>  
#include<cstring>  
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
    char prefixString[SIZE];  
    cout << "Enter Prefix Expression: ";  
    cin >> prefixString;  
  
    int len = strlen(prefixString);  
  
    for (int i = len - 1; i >= 0; i--) {   // ← traverse RIGHT TO LEFT  
        char ch = prefixString[i];  
  
        if (isdigit(ch)) {  
            resultStack.push(ch - '0');  
        } else {  
            int a = resultStack.topElement(); resultStack.pop();  //   a and b are  
            int b = resultStack.topElement(); resultStack.pop();  //   swapped vs postfix  
  
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
Enter Prefix Expression:*+23-54

Result: 5

Process finished with exit code 0
```