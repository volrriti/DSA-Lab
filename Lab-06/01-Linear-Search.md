# Linear Search
## Algorithm
1. Call function `index = linearSearch(a[], n, key)`
2. Inside `linearSearch(a[],n,key)`:
	1. Loop `i = 0` to `i < n`
		1. If `a[i] = key` return `i`
	2. Return `-1`
3. If `index = -1`, display not found
4. Else display `index`

## Program
```cpp
#include <iostream>
using namespace std;

int linearSearch(int a[], int n, int key) {
    for (int i = 0; i < n; i++) {
        if (a[i] == key) {
            return i;
        }
    }
    return -1;
}

int main() {
    int a[100]={1,2,3,4,5,6,7,8,10,12,14,66}, n=12, key, index;

    cout << "Enter element to search: ";
    cin >> key;

    index = linearSearch(a, n, key);

    if (index != -1) cout << "Element found at index " << index << endl;
    else cout << "Element not found in the array." << endl;
}
```
## Output
```
Enter element to search:12

Element found at index 9

Process finished with exit code 0
```
