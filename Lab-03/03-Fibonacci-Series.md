# Fibonacci Series up to n terms
## Algorithm
2. Read the value of `n`
3. Call the recursive function `fibo(n)`
4. In `fibo(n)`:
    1. If `n=0` or `n=1` return `1`
	2. Else return `fibo(n-1) + fibo(n-2)` 
5. Loop  `i=0` to `i<n`:
	1. Display `fibo(i)`

## Program
```cpp
#include<iostream>  
using namespace std;  
  
int fibo(int n) {  
    if(n==0 || n==1) return 1;  
    else return fibo(n-1)+fibo(n-2);  
}  
  
int main() {  
    int n;  
    cout << "Enter a number: ";  
    cin >> n;  
    cout << "Fibonacci Series: ";  
    for(int i=0; i<n; i++) {  
        cout << " " << fibo(i);  
    }  
}
```
## Output
```
Enter a number:10

Fibonacci Series:  1 1 2 3 5 8 13 21 34 55
Process finished with exit code 0
```