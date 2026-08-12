# Reverse of given String
## Algorithm
1. Read the string `str` 
2. Call the recursive function `rev(str, srt.length())`
3. In `rev(str,n)`:
    1. If `n < 0`, return
    2. Display `srt[n]`
    3. `rev(srt,n-1)`
## Program
```cpp
#include <iostream>  
using namespace std;  
  
void rev(string str, int n) {  
    if (n < 0)  return; 
    cout << str[n];  
    rev(str, n - 1);  
}  
  
int main() {  
    string str;  
    cout << "Enter a string: ";  
    cin >> str;  
    rev(str, str.length() - 1);  
}
```

## Output
```
Enter a string:wallah

hallaw
Process finished with exit code 0
```