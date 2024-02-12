```c++
#include<bits/stdc.h>
using namespace std;

int m[1000]; // Moved the counting array declaration outside the function

int maximum(int arr[], int n) {
    int max_val = INT_MIN; // Initialize to minimum possible value
    for (int i = 0; i < n; i++) {
        if (arr[i] > max_val) {
            max_val = arr[i];
        }
    }
    return max_val;
}

int minimum(int arr[], int n) {
    int min_val = INT_MAX; // Initialize to maximum possible value
    for (int i = 0; i < n; i++) {
        if (arr[i] < min_val) {
            min_val = arr[i];
        }
    }
    return min_val;
}

void Count_Sort(int arr[], int n) {
    int maxim = maximum(arr, n);
    int minim = minimum(arr, n);
    int range = maxim - minim + 1;

    if (minim > -1) {
        for (int i = 0; i < n; i++) {
            m[arr[i]]++;
        }
        for (int i = 0; i < range;) { // Use 'range' instead of 'maxim+1'
            if (m[i] == 0) {
                i++;
            }
            else {
                cout << i << endl;
                m[i]--;
            }
        }
    }
    else {
        for (int i = 0; i < n; i++) {
            m[arr[i] + abs(minim)]++;
        }
        for (int i = 0; i < range;) { // Use 'range' instead of 'maxim+abs(minim)'
            if (m[i] == 0) {
                i++;
            }
            else {
                cout << i + minim << endl;
                m[i]--;
            }
        }
    }
}

int main() {
    int arr[10] = {1, -2, 5, 7, 14, 2, 6, 9, 15, 10};
    Count_Sort(arr, 10);
    return 0;
}

```
