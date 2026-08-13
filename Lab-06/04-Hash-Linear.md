# Linear Probing Hash Table
## Algorithm
### Initiation and Insertion
1. Initiate a `table` with all elements `-1`
2. Read number of keys `n`
3. Loop `n` times:
	1. Read `key`
	2. Call `h.insert(key)`
4. In `insert(key)`:
	1. `index = key % SIZE`
	2. Loop while `table[index] != -1`; `index = (index+1) % size`
	3. `table[index] = key`
### Search
1. `index = key % SIZE`
2. `start = index`
3. Loop while  `table[index] != -1`;
	1. If `table[index] == key`
		1. Display element found at `index`
		2. Return
	2. `index = (index + 1) % size`
	3. if `index = start`  break
4. Display element not found
### Display
1. Loop `i = 0` to `i<size`:
	1. Display `i` 
	2. If `table[i] = -1` Display empty
	3. Else display `table[i]`
## Program
```cpp
#include <iostream>  
using namespace std;  
  
class HashTable {  
    int table[10];  
    int size=10;  
  
public:  
    HashTable() {  
        for (int i = 0; i < size; i++)  
            table[i] = -1;  
    } 
  
    void insert(int key) {  
        int index = key % size;  
  
        while (table[index] != -1) {  
            index = (index + 1) % size;  
        }  
  
        table[index] = key;  
    }  
  
    void search(int key) {  
        int index = key % size;  
        int start = index;  
  
        while (table[index] != -1) {  
            if (table[index] == key) {  
                cout << "Element found at index " << index << endl;  
                return;  
            }  
  
            index = (index + 1) % size;  
  
            if (index == start)  
                break;  
        }  
  
        cout << "Element not found." << endl;  
    }  
  
    void display() {  
        cout << "\nHash Table:\n";  
  
        for (int i = 0; i < size; i++) {  
            cout << i << " : ";  
  
            if (table[i] == -1)  
                cout << "Empty";  
            else  
                cout << table[i];  
  
            cout << endl;  
        }  
    }  
};  
  
int main() {  
    HashTable h;  
    int n, key;  
  
    cout << "Enter number of keys: ";  
    cin >> n;  
  
    cout << "Enter keys:\n";  
  
    for (int i = 0; i < n; i++) {  
        cin >> key;  
        h.insert(key);  
    }  
  
    h.display();  
  
    cout << "\nEnter key to search: ";  
    cin >> key;  
  
    h.search(key);  
}
```
## Output
```
Enter number of keys:9

Enter keys:
1

2

12

23

4

5

6

7

99


Hash Table:
0 : Empty
1 : 1
2 : 2
3 : 12
4 : 23
5 : 4
6 : 5
7 : 6
8 : 7
9 : 99

Enter key to search:5

Element found at index 6
```