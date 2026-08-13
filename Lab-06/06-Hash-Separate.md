# Separate Chaining Hash Table
## Algorithm
### Initiation and Insertion
1. Initiate a `table` containing `SIZE` linked-list heads
2. Set every `table[i] = NULL`
3. Read number of keys `n`
4. Loop `n` times:
    1. Read `key`
    2. Call `h.insert(key)`
5. In `insert(key)`:
    1. `index = key % SIZE`
    2. Create a new node containing `key`
    3. Set `newNode->next = table[index]`
    4. Set `table[index] = newNode`

### Search
1. `index = key % SIZE`
2. Set `temp = table[index]`
3. Loop while `temp != NULL`:
    1. If `temp->key == key`:
        1. Display element found at `index`
        2. Return
    2. `temp = temp->next`
4. Display element not found

### Display

1. Loop `i = 0` to `i < SIZE`
    1. Display `i`
    2. Set `temp = table[i]`
    3. Loop while `temp != NULL`
        1. Display `temp->key
        2. `temp = temp->next`
    4. Display `NULL`
## Program
```cpp
#include <iostream>
using namespace std;

class HashTable {
    struct Node {
        int key;
        Node* next;

        Node(int k) {
            key = k;
            next = NULL;
        }
    };

    Node* table[10];
    int size = 10;

public:
    HashTable() {
        for (int i = 0; i < size; i++)
            table[i] = NULL;
    }

    int hashFunction(int key) {
        return key % size;
    }

    void insert(int key) {
        int index = hashFunction(key);

        Node* newNode = new Node(key);
        newNode->next = table[index];
        table[index] = newNode;
    }

    void search(int key) {
        int index = hashFunction(key);
        Node* temp = table[index];

        while (temp != NULL) {
            if (temp->key == key) {
                cout << "Element found at index " << index << endl;
                return;
            }

            temp = temp->next;
        }

        cout << "Element not found." << endl;
    }

    void display() {
        cout << "\nHash Table:\n";

        for (int i = 0; i < size; i++) {
            cout << i << " : ";

            Node* temp = table[i];

            while (temp != NULL) {
                cout << temp->key << " -> ";
                temp = temp->next;
            }

            cout << "NULL" << endl;
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

```