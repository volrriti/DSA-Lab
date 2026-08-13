# Topic
## Algorithm
### Initiation and Insertion

1. Initiate a `table` with all elements `-1`
2. Read number of keys `n`
3. Loop `n` times:
    1. Read `key`
    2. Call `h.insert(key)`
4. In `insert(key)`
    1. `h1 = key % SIZE`
    2. `h2 = 7 - (key % 7)`
    3. `i = 0`
    4. `index = h1`
    5. Loop while `table[index] != -1`:
        1. `i++`
        2. `index = (h1 + i*h2) % SIZE`
    6. `table[index] = key`

### Search

1. `h1 = key % SIZE`
2. `h2 = 7 - (key % 7)`
3. `i = 0`
4. `index = h1`
5. Loop while `table[index] != -1`:
    1. If `table[index] == key`
        1. Display element found at `index`
        2. Return
    2. `i++`.
    3. `index = (h1 + i*h2) % SIZE`
6. Display element not found

### Display

1. Loop `i = 0` to `i < SIZE`:
    1. Display `i`
    2. If `table[i] == -1`, display `Empty`
    3. Else display `table[i]`
## Program
```cpp
#include <iostream>
using namespace std;

class HashTable {
    int table[10];
    int size = 10;

public:
    HashTable() {
        for (int i = 0; i < size; i++)
            table[i] = -1;
    }

    int hashFunction1(int key) {
        return key % size;
    }

    int hashFunction2(int key) {
        return 7 - (key % 7);
    }

    void insert(int key) {
        int h1 = hashFunction1(key);
        int h2 = hashFunction2(key);
        int index;
        int i = 0;

        while (i < size) {
            index = (h1 + i * h2) % size;

            if (table[index] == -1) {
                table[index] = key;
                return;
            }

            i++;
        }

        cout << "Hash table is full." << endl;
    }

    void search(int key) {
        int h1 = hashFunction1(key);
        int h2 = hashFunction2(key);
        int index;
        int i = 0;

        while (i < size) {
            index = (h1 + i * h2) % size;

            if (table[index] == -1)
                break;

            if (table[index] == key) {
                cout << "Element found at index " << index << endl;
                return;
            }

            i++;
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

    return 0;
}
```