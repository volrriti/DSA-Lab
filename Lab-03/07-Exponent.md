# Finding Exponent
## Algorithm
1. Read the value of `x` and `n` 
2. Call the recursive function `exp(x, n)`
3. In `exp(x,n)`:
    1. If `n == 1`, return `x`
    2. Else return `x + exp(x, n-1)`
4. Display `exp(x,n)`

## Program
```cpp
#include<iostream>  
using namespace std;  
  
int exp(int x, int n) {  
    if(n==1) return x;  
    return x * exp(x, n-1);  
}  
  
int main() {  
    int x, n;  
    cout << "Enter a number: ";  
    cin >> x;  
    cout << "Enter exponent: ";  
    cin >> n;  
    cout << "Result: " << exp(x,n) <<endl;  
}
```
## Output
```
Enter a number:2

Enter exponent:3

Result: 8

Process finished with exit code 0
```