# List using Array
Features
- insert
- delete
- update
- merge
- traverse
## Algorithm
### Insert
1. Loop `i=n` to `i>=pos` with `i--`:
	1. Shift `list[i] = list[i-1]`
2. Put `list[pos-1] = value`
3. n++
### Delete
1. Loop `i= pos-1` to `i < n - 1` with `i++`:
	1. Shift `list[i] = list[i + 1]`
2. n--
### Update
1. `list[pos - 1] = value`
### Merge
1. Loop `i=0` to `i < size of new array`:
	1. `list[n] = newarray[i]`
	2. `n++`
### Traverse
1. Loop `i=0` to `i<n`:
	1. Display `list[i]`
## Program
```cpp
#include<iostream>  
using namespace std;  
  
#define SIZE 15  
  
class List {  
    int n = 0;
    int list[SIZE];  
    public:  
        List() {}  
        void insert(int pos, int value) {
	        for(int i = n; i >= pos; i--) {
		        list[i] = list[i - 1];
			} 
			list[pos - 1] = value; 
			n++;
		}  
        void deleteElement(int pos) {
	        for(int i = pos - 1; i < n - 1; i++){
		        list[i] = list[i + 1];
			} 
			n--;
		}
        void update(int pos, int value){
	        list[pos - 1] = value;
	    }
	    void merge(int arr[], int size){
			for(int i = 0; i < size; i++) {
				list[n] = arr[i];
				n++;
			}
		}
		void traverse() {
			for(int i = 0; i < n; i++) {
				cout << list[i] << " ";
			}
		}
};  
```
