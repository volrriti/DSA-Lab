# Recursive Binary Search
## Algorithm
1. Call recursive function `index = binarySearch(a[], low, high, key)`
2. Inside `binarySearch(a[], low, high, key)`:
	1. If `low > high` return `-1`
	2. `mid = (low + high) / 2`
	3. if `a[mid] == key` return `mid`
	4. else if return `binarySearch(a, low, mid - 1, key)`
	5. else `return binarySearch(a, mid + 1, high, key)`
3. If `index = -1`, display not found
4. Else display `index`
## Program
```cpp
#include <iostream>
using namespace std;
int binarySearch(int a[], int low, int high, int key) {
	if (low > high) return -1;
	int mid = (low + high) / 2;
	if (a[mid] == key) return mid;
	else if (key < a[mid]) return binarySearch(a, low, mid - 1, key);
	else return binarySearch(a, mid + 1, high, key);
}
int main() {  
    int a[100]={1,2,3,4,5,6,7,8,10,12,14,66}, n=12, key, index;  
  
    cout << "Enter element to search: ";  
    cin >> key;  
  
    index = binarySearch(a, 0, n-1, key);  
  
    if (index != -1) cout << "Element found at index " << index << endl;
    else cout << "Element not found in the array." << endl;
}
```
## Output
```
Enter element to search:2

Element found at index 1

Process finished with exit code 0
```