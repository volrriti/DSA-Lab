# Iterative Binary Search
## Algorithm
1. Call function `index = binarySearch(a[], n, key)`
2. Inside `binarySearch(a[],n,key)`:
	1. Set `low = 0`, `high = n-1`
	2. Loop while `low <= high`
		1. `mid = (low + high) / 2`
		2. if `a[mid] == key` return `mid`
		3. else if `a[mid] < key` `high = mid - 1`
		4. else `low = mid + 1`
	3. Return `-1`
3. If `index = -1`, display not found
4. Else display `index`
## Program
```cpp
#include <iostream>  
using namespace std;  
  
int binarySearch(int a[], int n, int key) {  
    int low = 0, high = n - 1;  
  
    while (low <= high) {  
        int mid = (low + high) / 2; 
        if (a[mid] == key) return mid;  
        else if (key < a[mid]) high = mid - 1;  
        else low = mid + 1;  
    }  
    return -1;  
}  
  
int main() {  
    int a[100]={1,2,3,4,5,6,7,8,10,12,14,66}, n=12, key, index;  
  
    cout << "Enter element to search: ";  
    cin >> key;  
  
    index = binarySearch(a, n, key);  
  
    if (index != -1) cout << "Element found at index " << index << endl;
    else cout << "Element not found in the array." << endl;
}
```
## Output
```
Enter element to search:8

Element found at index 7

Process finished with exit code 0
```