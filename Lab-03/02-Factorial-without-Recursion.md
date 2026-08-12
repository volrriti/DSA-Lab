# Factorial of a Number without Recursion
## Algorithm
1. Input a number `n`
2. Let `fac = 1`
3. Loop  `i=0` to `i<n`:
	1. `fac = fac * i`
4. Display `fac`
## Program
```cpp
#include<iostream>  
using namespace std;  
  
int main() {  
    int n, fac=1;  
    cout << "Enter a number: ";  
    cin >> n;  
    for (int i = 1; i <= n; i++) {  
        fac *= i;  
    }  
    cout << "Factorial: "<<n<<endl;  
}
```
## Output
```
Enter a number:5

Factorial: 5

Process finished with exit code 0

```