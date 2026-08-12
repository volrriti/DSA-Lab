# Circular Queue
## Algorithm
### Enqueue
1. Check for Overflow; if `(rear+1) % MAX = front`
2. If `front = -1`, `front = 0`
3. `rear = (rear+1) % MAX`
4. Add value at `queue[rear]`
### Dequeue
1. Check for Underflow; if `front = -1`
2. Display `queue[front]` was deleted.
3. If `front = rear`:`front=rear=-1`
   Else `front = (front + 1) % MAX`
### Display
1.  Check for Underflow; if `front = -1`
2. Set `i = front`
3. Loop While `i != rear`:
	1. Display `queue[i]`
	2. `i = (i+1) % MAX`
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
            if ((rear+1) % MAX == front) {  
                cout << "Queue Overflow" << endl;  
	            return;
            }
            if (front == -1) front = 0;
            rear = (rear+1) % MAX;
            queue[rear] = value;  
        }  
        void dequeue() {  
            if (front == -1) {  
                cout << "Stack Underflow" << endl;  
                return;
            }
            cout << queue[front] << " was deleted." << endl;  
            if(front == rear) {
	            front = -1;
	            rear = -1;
	        } else {
		        front = (front + 1) % MAX
	        }
        }  
  
        void display() {  
            if (front == -1) {  
                cout << "Empty Queue" << endl;  
                return;
            }  
			cout << "Stack: "; 
			int i = front; 
			while (i != rear){
				cout << queue[i] << " ";
				i = (i + 1)%MAX;
			}
        }  
};  
```