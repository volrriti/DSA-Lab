# Implementation of Stack using Array

## Algorithm:

**Push:**
1. Start
2. Check for Stack Overflow
3. Ask user for `data`
4. `top = top + 1`
5. `stack[top] = data`
6. End

**Pop:**
1. Start
2. Check for Stack Underflow
3. `top=top-1`
4. End

**Display:**
1. Start
2. Check for Empty Stack
3. Loop from `i = top` to `i = 0`
	1. Display `stack[i]`
4. End

**Main**
1. Start
2. Create `Stack s` Object
3. Display choices
4. Input `choice`
5. Use switch case to choose choices
6. End


---
## Program:

```cpp
#include<iostream>  
using namespace std;  
  
#define SIZE 15  
  
class Stack {  
    int top = -1;  
    int stack[SIZE];  
    public:  
        Stack() {}  
        void push() {  
            if (top == SIZE - 1) {  
                cout << "Stack Overflow" << endl;  
            }else{  
                int data;  
                cout << "Enter Data: ";  
                cin >> data;  
                stack[++top] = data;  
                cout << data << " was pushed." << endl;  
            }  
        }  
        void pop() {  
            if (top == -1) {  
                cout << "Stack Underflow" << endl;  
            }else {  
                cout << stack[top--] << " was popped." << endl;  
            }  
        }  
  
        void display() {  
            if (top == -1) {  
                cout << "Empty Stack" << endl;  
            }else {  
                cout << "Stack: ";  
                for (int i = top; i >= 0; i--) {  
                    cout << stack[i] << " ";  
                }  
            }  
        }  
};  
  
int main() {  
    Stack s;  
    int choice;  
    cout << "\n1. Push\n2. Pop\n3. Display\n4. Exit";  
    do {  
        cout << "\nEnter your choice: ";  
        cin >> choice;  
        switch (choice) {  
            case 1:  
                s.push();  
                break;  
            case 2:  
                s.pop();  
                break;  
            case 3:  
                s.display();  
                break;  
            case 4:  
                exit(1);  
                break;  
            default:  
                cout << "Invalid Choice" << endl;  
        }  
    }while (1);  
}
```

---

## Output

```
1. Push
2. Pop
3. Display
4. Exit
   
Enter your choice:1
Enter Data:1
1 was pushed.

Enter your choice:2
1 was popped.

Enter your choice:1
Enter Data:1
1 was pushed.

Enter your choice:1
Enter Data:3
3 was pushed.

Enter your choice:3
Stack: 3 1

Enter your choice:4

Process finished with exit code 1
```
