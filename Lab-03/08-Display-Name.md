# Display Name Thrice
## Algorithm
1. Read `name` 
2. Call the recursive function `display(name)`
3. In `display(str, n=3)`:
    1. If `n == 0`, return
    2. Else display `str` 
    3. Call `display(str, n-1)`
## Program
```cpp
#include <iostream>  
using namespace std;  
  
void display(string str, int n=3) {  
    if (n == 0) return;  
    cout << str << endl;  
    display(str, n - 1);  
}
  
int main() {  
    string name;  
    cout << "Enter your name: ";  
    cin >> name;  
    display(name);  
}
```
## Output
```
Enter your name:Aayam

Aayam
Aayam
Aayam

Process finished with exit code 0
```