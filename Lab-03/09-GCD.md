# GCD of Two Numbers
## Algorithm
1. Read integers `a`, `b`
2. Call the recursive function `gcd(a, b)`
3. In `gcd(a,b)`:
	1. If `b == 0` return `a`;
	2. Else return `gcd(b, a%b)`
4. Display `gcd(a,b)`
## Program
```cpp
#include <iostream>  
using namespace std;  
  
int gcd(int a, int b) {  
    if (b == 0) return a;  
    return gcd(b, a % b);  
}  
  
int main() {  
    int a, b;  
    cout << "Enter Two Numbers: ";  
    cin >> a >> b;  
    cout << "GCD: "<< gcd(a,b)<<endl;  
}
```
## Output
```
Enter Two Numbers:144 96

GCD: 48

Process finished with exit code 0
```