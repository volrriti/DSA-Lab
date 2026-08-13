# Topic
## Algorithm
1. Read number of elements `n`
2. Read elements in `a[]`
3. Call `quicksort(a, 0, n-1)`
4. In `quickSort(a, low, high)`:
	1. If `low < high`;
		1. `p = partition(a, low, high)`
		2.  `quickSort(a, low, p - 1)`
		3. `quickSort(a, p + 1, high)`
5. In `partition(a[], low, high)`:
	1. `pivot = a[high]`
	2. `i = low - 1 `
	3. Loop from `j = low; j < high; j++`:
		1. If `a[j] < pivot`:
			1. `i++`
			2. Swap `a[j]` and `a[i]`
	4. Swap `a[i+1]` and `a[high]`
	5. Return `i + 1`
## Program
```cpp
#include <iostream>
using namespace std;

int partition(int a[], int low, int high) {
    int pivot = a[high];
    int i = low - 1;

    for (int j = low; j < high; j++) {
        if (a[j] < pivot) {
            i++;
            swap(a[i], a[j]);
        }
    }

    swap(a[i + 1], a[high]);

    return i + 1;
}

void quickSort(int a[], int low, int high) {
    if (low < high) {
        int p = partition(a, low, high);

        quickSort(a, low, p - 1);
        quickSort(a, p + 1, high);
    }
}

int main() {
    int a[100], n;

    cout << "Enter number of elements: ";
    cin >> n;

    cout << "Enter elements: ";
    for (int i = 0; i < n; i++)
        cin >> a[i];

    quickSort(a, 0, n - 1);

    cout << "Sorted array: ";
    for (int i = 0; i < n; i++)
        cout << a[i] << " ";
}
```
## Output
```
Enter number of elements:5

Enter elements:1

2

4

3

5

Sorted array: 1 2 3 4 5
Process finished with exit code 0
```