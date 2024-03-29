```c++
// Binary search to find the correct position to insert the key
int binarySearch(int arr[], int key, int low, int high) {
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (arr[mid] == key) {
            return mid;
        } else if (arr[mid] < key) {
            low = mid + 1;
        } else {
            high = mid - 1;
        }
    }
    return low;
}

void insertionSort(int arr[], int n) {
    for (int i = 1; i < n; ++i) {
        int key = arr[i];
        int j = i - 1;

        // Find the correct position for key using binary search
        int pos = binarySearch(arr, key, 0, j);

        // Move elements to make space for key
        while (j >= pos) {
            arr[j + 1] = arr[j];
            j--;
        }
        // Insert key at its correct position
        arr[pos] = key;
    }
}
```