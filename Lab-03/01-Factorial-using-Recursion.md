# Factorial of a Number using Recursion
## Algorithm:
2. Read the value of `n`
3. Call the recursive function `factorial(n)`
4. In `factorial(n)`:
    1. If `n=0` return `1`
	2. Else return `n * factorial(n-1) 
5. Display `factorial(n)`
## Program
```cpp
#include<iostream>  
using namespace std;  
  
int factorial(int n) {  
    if(n==0) return 1;  
    else return n*factorial(n-1);  
}  
  
int main() {  
    int n;  
    cout << "Enter a number: ";  
    cin >> n;  
    cout << "Factorial: "<<factorial(n)<<endl;  
}
```
## Output
```
Enter a number:5

Factorial: 120

Process finished with exit code 0
```