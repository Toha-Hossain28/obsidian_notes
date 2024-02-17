## C standard
```c++
#include <iostream>
using namespace std;

struct Node {
    int val;
    Node* next;
};

void bucketSort(int arr[], int n) {
    // Find maximum element in the array
    int max = arr[0];
    for (int i = 1; i < n; i++) {
        if (arr[i] > max) {
            max = arr[i];
        }
    }

    // Create buckets and initialize them to nullptr
    Node** p = new Node*[max + 1]();
    
    // Insert elements into buckets
    for (int i = 0; i < n; i++) {
        int index = arr[i];
        Node* newNode = new Node;
        newNode->val = arr[i];
        newNode->next = nullptr;

        if (p[index] == nullptr) {
            p[index] = newNode;
        } else {
            Node* ptr = p[index];
            while (ptr->next != nullptr) {
                ptr = ptr->next;
            }
            ptr->next = newNode;
        }
    }

    // Reconstruct the sorted array from buckets
    int j = 0;
    for (int i = 0; i <= max; i++) {
        Node* ptr = p[i];
        while (ptr != nullptr) {
            arr[j++] = ptr->val;
            Node* temp = ptr;
            ptr = ptr->next;
            delete temp; // Free memory
        }
    }

    // Free memory allocated for buckets
    delete[] p;
}

int main() {
    int n;
    cin >> n;
    int arr[n];
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }

    bucketSort(arr, n);

    // Print sorted array
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    return 0;
}

```