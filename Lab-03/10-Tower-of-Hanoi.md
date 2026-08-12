# Tower of Hanoi
## Algorithm
1. Read number of discs `n`
2. Call the recursive function `toh(n, 'A', 'B', 'C')`
3. In `toh(n, src, aux, dst)`:
	1. If `n=1`:
		1. Display `src` to `dst`
		2. Return
	2. Call `toh(n-1,src,dst,aux)`
	3. Display `src` to `dst`
	4. Call `toh(n-1,aux,src,dst)`
## Program
```cpp
#include <iostream>  
#include <numeric>  
using namespace std;  
  
void toh(int n, char src, char aux, char dst) {  
    if(n==1) {  
        cout << src << " to " << dst << endl;  
        return;  
    }  
    toh(n-1, src, dst, aux);  
    cout << src << " to " << dst<< endl;  
    toh(n-1, aux, src, dst);  
}  
  
int main() {  
    int n;  
    cout << "Enter Number of Disks: ";  
    cin >> n;  
    toh(n, 'A', 'B', 'C');  
}
```
## Output
```
Enter Number of Disks:3

A to C
A to B
C to B
A to C
B to A
B to C
A to C

Process finished with exit code 0
```