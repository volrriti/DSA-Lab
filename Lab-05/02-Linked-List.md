# Linked List
Features
- Insert node at beginning
- Insert at given position
- Insert at last
- Delete first node
- Delete last node
- Delete nth node
- Count nodes
- Display items
- Search items

## Algorithm
### Inserting at Beginning
1. Create a new node `newnode` with data at `newnode->data`
2. Point `newnode->next` to `head`
3. Point `head` to `newnode`
### Inserting at Given Position
1. Create a new node `newnode` with data at `newnode->data`
2. If `pos = 1`, *Insert at Beginning*
3. Create a node pointer `*temp = head`
4. Loop `i = 1` while `i < pos - 1`: `temp = temp->next`
5. Point `newnode->next = temp->next` 
6. Point `temp->next = newnode`
### Inserting at Last
1. Create a new node `newnode` with data at `newnode->data`
2. If `head = NULL`, Point `head = newnode` and return
3. Loop while `temp->next != NULL`; `temp = temp->next`
4. Point `temp->next = newnode`
### Deleting First
1. Create a node pointer `*temp = head`
2. Point `head = head->next`
3. Delete `temp`
### Deleting at Position
1. If `pos = 1`, *Delete First*
2. Create a node pointer `*temp = head` and `*prev`
3. Loop `i = 1` while `i < pos - 1`:
	1. `prev = temp`
	2. `temp = temp->next`
4. Point `prev->next = temp->next`
5. Delete `temp`
### Deleting Last
1. If `head->next = NULL`:
	1. Delete `head`
	2. Point `head = NULL`
	3. Return
2. Create a node pointer `*temp = head` and `*prev`
3. Loop while `temp->next != NULL`; 
	1. Point `prev = temp`
	2. Point `temp = temp->next`
4. Point `prev->next = temp->next`
5. Delete `temp`
### Count Nodes
1. Set `count = 0`
2. Create a node pointer `*temp = head`
3. Loop while `temp->next != NULL`; 
	1. Point `temp = temp->next`
	2. `count = count + 1`
4. Display `count`
### Display Items
1. Create a node pointer `*temp = head`
2. Loop while `temp->next != NULL`
	1. Point `temp = temp->next`
	2. Display `temp->data`
### Search
1. Ask for data `value`
2. Set `pos = 1`
3. Loop while `temp->next != NULL`
	1. Point `temp = temp->next`
	2. If `temp->data = value`, display `pos`
	3. `pos++`
	4. Return
4. Display data not found
## Program
```cpp
#include <iostream>  
using namespace std;  
  
struct Node  
{  
    int data;  
    Node *next;  
};  
Node *head = NULL;  
  
  
Node* createNode(int value){  
    Node *newNode = new Node;  
  
    newNode->data = value;  
    newNode->next = NULL;  
  
    return newNode;  
}  
  
void insertFirst(int value){  
    Node *newNode = createNode(value);  
    newNode->next = head;  
    head = newNode;  
}  
  
void insertPosition(int value, int pos){  
    if(pos == 1)  
    {  
        insertFirst(value);  
        return;  
    }  
  
    Node *newNode = createNode(value);  
    Node *temp = head;  
    for(int i = 1; i < pos - 1 && temp != NULL; i++)  
    {  
        temp = temp->next;  
    }  
  
    newNode->next = temp->next;  
    temp->next = newNode;  
}  
  
  
void insertLast(int value){  
    Node *newNode = createNode(value);  
  
    if(head == NULL)  
    {  
        head = newNode;  
        return;  
    }  
  
    Node *temp = head;  
  
    while(temp->next != NULL)  
    {  
        temp = temp->next;  
    }  
  
    temp->next = newNode;  
}  
  
  
void deleteFirst(){  
    if(head == NULL)  
    {  
        cout << "List Empty\n";  
        return;  
    }  
  
    Node *temp = head;  
    head = head->next;  
    delete temp;  
}  
  
  
void deleteLast(){  
    if(head == NULL)  
    {  
        cout << "List Empty\n";  
        return;  
    }  
  
    if(head->next == NULL)  
    {  
        delete head;  
        head = NULL;  
        return;  
    }  
  
    Node *temp = head;  
    Node *prev;  
  
    while(temp->next != NULL)  
    {  
        prev = temp;  
        temp = temp->next;  
    }  
  
    prev->next = NULL;  
  
    delete temp;  
}  
  
  
void deletePosition(int pos){  
    if(head == NULL)  
    {  
        cout << "List Empty\n";  
        return;  
    }  
  
    if(pos == 1)  
    {  
        deleteFirst();  
        return;  
    }  
  
    Node *temp = head;  
    Node *prev;  
  
    for(int i = 1; i < pos && temp != NULL; i++)  
    {  
        prev = temp;  
        temp = temp->next;  
    }  
  
    if(temp == NULL)  
    {  
        cout << "Invalid position\n";  
        return;  
    }  
  
    prev->next = temp->next;  
  
    delete temp;  
}  
  
void countNodes(){  
    Node *temp = head;  
    int count = 0;  
  
    while(temp != NULL)  
    {  
        count++;  
        temp = temp->next;  
    }  
  
    cout << "Number of nodes = " << count << endl;  
}  
  
void display(){  
    if(head == NULL)  
    {  
        cout << "List Empty\n";  
        return;  
    }  
  
    Node *temp = head;  
  
    while(temp != NULL)  
    {  
        cout << temp->data << " ";  
        temp = temp->next;  
    }  
  
    cout << endl;  
}  
  
  
void search(int value){  
    Node *temp = head;  
    int pos = 1;  
  
    while(temp != NULL)  
    {  
        if(temp->data == value)  
        {  
            cout << "Item found at position " << pos << endl;  
            return;  
        }  
  
        temp = temp->next;  
        pos++;  
    }  
  
    cout << "Item not found\n";  
}  
  
  
int main(){  
    int choice, value, pos;  
  
    while(true)  
    {  
        cout << "\n--- LINKED LIST ---\n";  
        cout << "1. Insert at beginning\n";  
        cout << "2. Insert at position\n";  
        cout << "3. Insert at last\n";  
        cout << "4. Delete first node\n";  
        cout << "5. Delete last node\n";  
        cout << "6. Delete nth node\n";  
        cout << "7. Count nodes\n";  
        cout << "8. Display items\n";  
        cout << "9. Search item\n";  
        cout << "10. Exit\n";  
  
        cout << "Enter choice: ";  
        cin >> choice;  
  
        switch(choice)  
        {  
            case 1:  
                cout << "Enter value: ";  
                cin >> value;  
                insertFirst(value);  
                break;  
  
            case 2:  
                cout << "Enter value: ";  
                cin >> value;  
                cout << "Enter position: ";  
                cin >> pos;  
                insertPosition(value, pos);  
                break;  
  
            case 3:  
                cout << "Enter value: ";  
                cin >> value;  
                insertLast(value);  
                break;  
  
            case 4:  
                deleteFirst();  
                break;  
  
            case 5:  
                deleteLast();  
                break;  
  
            case 6:  
                cout << "Enter position: ";  
                cin >> pos;  
                deletePosition(pos);  
                break;  
  
            case 7:  
                countNodes();  
                break;  
  
            case 8:  
                display();  
                break;  
  
            case 9:  
                cout << "Enter value to search: ";  
                cin >> value;  
                search(value);  
                break;  
  
            case 10:  
                return 0;  
  
            default:  
                cout << "Invalid choice\n";  
        }  
    }  
}
```
