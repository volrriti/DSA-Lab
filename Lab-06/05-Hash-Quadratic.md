# Quadratic Probing Hash Table
## Algorithm
### Initiation and Insertion
1. Initiate a `table` with all elements `-1`
2. Read number of keys `n`
3. Loop `n` times:
	1. Read `key`
	2. Call `h.insert(key)`
4. In `insert(key)`:
	1. `h = key % SIZE`, `i=1`
	2. `index = h`
	3. Loop while `table[index] != -1`
		1. `index = (h + i*i) % size`
		2. `i++`
	4. `table[index] = key`
### Search
1. `h = key % SIZE`
2. `index = h`, `start = index`
3. `i = 1`
4. Loop while  `table[index] != -1`;
	1. If `table[index] == key`
		1. Display element found at `index`
		2. Return
	2. `index = (h + i*i) % size`
	3. `i++`
	4. if `index = start`  break
5. Display element not found
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
        int h = key % size;
        int index = h;
        int i = 1;
        while (table[index] != -1) {  
            index = (h + i*i) % size;  
            i++;
        }  
  
        table[index] = key;  
    }  
  
    void search(int key) {  
        int h = key % size;  
        int index = h;
        int start = index;  
        int i = 1;
  
        while (table[index] != -1) {  
            if (table[index] == key) {  
                cout << "Element found at index " << index << endl;  
                return;  
            }  
            index = (h + i*i) % size;  
			i++;
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
  
    cout << "Enter number of keys: " << endl;  
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
Enter number of keys:
5

Enter keys:
1

1

2

3

4


Hash Table:
0 : Empty
1 : 1
2 : 1
3 : 2
4 : 3
5 : 4
6 : Empty
7 : Empty
8 : Empty
9 : Empty

Enter key to search:4

Element found at index 5

Process finished with exit code 0

```
