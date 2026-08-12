# Linear Queue
## Algorithm
### Enqueue
1. Check for Overflow; if `rear = MAX - 1`
2. If `front = -1`, `front = 0`
3. `rear++`
4. Add value at `queue[rear]`
### Dequeue
1. Check for Underflow; if `front = -1`
2. Display `queue[front]` was deleted.
3. `front++`
4. If `front > rear`: `front = rear = -1`
### Display
1.  Check for Underflow; if `front = -1`
2. Loop from `i=front` to `i=rear`: Display `queue[i]`
## Program
```cpp
#include<iostream>  
using namespace std;  
  
#define SIZE 15  
  
class Queue {  
    int front = -1;
    int rear = -1;  
    int queue[SIZE];  
    public:  
        Queue() {}  
        void enqueue(int value) {  
            if (rear == MAX - 1) {  
                cout << "Queue Overflow" << endl;  
	            return;
            }
            if (front == -1) front = 0
            queue[++rear] = value;  
        }  
        void dequeue() {  
            if (front == -1) {  
                cout << "Stack Underflow" << endl;  
                return;
            }
            cout << queue[front] << " was deleted." << endl;  
            front++;
            if(front > rear) {
	            front = -1;
	            rear = -1;
	        }
        }  
  
        void display() {  
            if (front == -1) {  
                cout << "Empty Queue" << endl;  
                return;
            }  
			cout << "Stack: ";  
			for (int i = front; i < = rear; i++) {  
				cout << queue[i] << " ";  
			}  
        }  
};  
```