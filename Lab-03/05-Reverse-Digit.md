# Reverse of given Digit
## Algorithm
1. Read the value of `n`
2. Call the recursive function `rev(n)`
3. In `rev(n, r=0)`:
    1. If `n == 0`, return `r`
    2. Else return `rev(n / 10, r * 10 + n%10)`
4. Display `rev(n)`
## Program
```cpp
#include <iostream>  
using namespace std;  
  
int rev(int n, int r=0) {  
    if (n == 0)  return r;  
    return rev(n / 10, r * 10 + n % 10);  
}  
  
int main() {  
    int n;  
    cout << "Enter a number: ";  
    cin >> n;  
    cout << "Reverse of " << n << " : " << rev(n) << endl;
}
```
## Output
```
Enter a number:1234

Reverse of 1234 : 4321

Process finished with exit code 0
```