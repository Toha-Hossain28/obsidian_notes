
### YT-Link: [heap](https://youtu.be/t0Cq6tVNRBA?si=TTqyu5LEPCn_mhW1)

```c++
#include<bits/stdc++.h>
using namespace std;


struct min_Heap {

    int arr[1000000];
    int size = 0;


    bool empty() {
        return size == 0;
    }

    bool hasLeft( int i ) {
        return 2 * i + 1 < size;
    }

    bool hasRight( int i ) {
        return 2 * i + 2 < size;
    }

    bool hasParent( int i ) {
        return i > 0;
    }

    int getLeftIndex( int i ) {
        return 2 * i + 1;
    }

    int getRightIndex( int i ) {
        return 2 * i + 2;
    }

    int getParentIndex( int i ) {
        return ( i - 1 ) / 2;
    }



    void insert( int v ) {

        arr[size++] = v;

        heapifyUp( size - 1 );
    }

    int extract() {
        if( size == 0) {
            return -1;
        }

        int val = arr[0];
        arr[0] = arr[size - 1];

        size--;
        heapifyDown( 0 );
        return val;
    }

    int peek() {
        return arr[0];
    }

    void heapifyUp( int i ) {
        while ( hasParent(i) && i > 0 && arr[i] < arr[getParentIndex( i )] ) {
            swap( arr[i], arr[getParentIndex( i )] );
            i = getParentIndex( i );
        }
    }

    void heapifyDown( int i ) {
        while ( hasLeft( i ) ) {
            int smallerChild = getLeftIndex( i );
            if ( hasRight( i ) && arr[getRightIndex( i )] < arr[getLeftIndex( i )] ) {
                smallerChild = getRightIndex( i );
            }

            if ( arr[i] < arr[smallerChild] ) {
                break;
            } else {
                swap( arr[i], arr[smallerChild] );
            }

            i = smallerChild;
        }
    }

    void deleteKey( int i ) {
        int keyIndex = -1;
        for (int j = 0; j < size; j++)
        {
            if(arr[j] == i) {
                keyIndex = j;
            }
        }
        swap(arr[keyIndex], arr[size - 1]);
        size--;
        heapifyDown(keyIndex);
    }
};

struct max_heap {

    int arr[1000000];
    int size = 0;

    bool empty() {
        return size == 0;
    }

    bool hasLeft( int i ) {
        return 2 * i + 1 < size;
    }

    bool hasRight( int i ) {
        return 2 * i + 2 < size;
    }

    bool hasParent( int i ) {
        return i > 0;
    }

    int getLeftIndex( int i ) {
        return 2 * i + 1;
    }

    int getRightIndex( int i ) {
        return 2 * i + 2;
    }

    int getParentIndex( int i ) {
        return ( i - 1 ) / 2;
    }

    void insert( int v ) {
        arr[size++] = v;
        heapifyUp( size - 1 );
    }

    int extract() {
        if( size == 0) {
            return -1;
        }

        int val = arr[0];
        arr[0] = arr[size - 1];

        size--;
        heapifyDown( 0 );
        return val;
    }

    int peek() {
        return arr[0];
    }

    void heapifyUp( int i ) {
        while ( hasParent(i) && i > 0 && arr[i] > arr[getParentIndex( i )] ) {
            swap( arr[i], arr[getParentIndex( i )] );
            i = getParentIndex( i );
        }
    }

    void heapifyDown( int i ) {
        while ( hasLeft( i ) ) {
            int largerChild = getLeftIndex( i );
            if ( hasRight( i ) && arr[getRightIndex( i )] > arr[getLeftIndex( i )] ) {
                largerChild = getRightIndex( i );
            }

            if ( arr[i] > arr[largerChild] ) {
                break;
            } else {
                swap( arr[i], arr[largerChild] );
            }

            i = largerChild;
        }
    }

};

int main() {
    min_Heap h;
    int q;
    cin >> q;
    while(q--) {
        int command;
        cin >> command;
        if( command == 1 ) {
            int x;
            cin >> x;
            h.insert(x);
        } else if( command == 2 ) {
            int x;
            cin >> x;
            h.deleteKey(x);
        } else if( command == 3 ) {
            cout << h.peek() << endl;
        }
    }
    return 0;
}
```