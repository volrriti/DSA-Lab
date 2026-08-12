# Sum of n Natural Numbers
## Algorithm
1. Read the value of `n`
2. Call the recursive function `sum(n)`
3. In `sum(n)`:
    1. If `n == 0`, return `1`
    2. Else return `n + sum(n-1)`
4. Display `sum(n)`

## Program
```cpp
#include<iostream>  
using namespace std;  
  
int sum(int n) {  
    if(n==0) return 1;  
    else return n+sum(n-1);  
}  
  
int main() {  
    int n;  
    cout << "Enter a number: ";  
    cin >> n;  
    cout << "Sum of " << n << " Natural Numbers : "<<sum(n)<<endl;  
}
```
## Output
```
Enter a number:10

Sum of 10 Natural Numbers : 56

Process finished with exit code 0
```