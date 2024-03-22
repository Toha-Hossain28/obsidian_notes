```c++
#include<bits/stdc++.h>
using namespace std;

float mySqrt(float x) {
    if (x == 0 || x == 1) {
        return x;
    }
    float low = 1.0;
    float high = x;
    float result = 0.0;
    while (low <= high) {
        float mid = (low + high) / 2.0;
        if (mid * mid <= x) {
            result = mid;
            low = mid + 0.00001; // Adjust by a small increment
        } else {
            high = mid - 0.00001;
        }
    }
    return result;
}

int main(){
    int x = 2;
    cout << mySqrt(x) << endl;
}
```
