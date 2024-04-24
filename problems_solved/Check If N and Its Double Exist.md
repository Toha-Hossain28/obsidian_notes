https://leetcode.com/problems/check-if-n-and-its-double-exist/

Given an array `arr` of integers, check if there exist two indices `i` and `j` such that :

- `i != j`
- `0 <= i, j < arr.length`
- `arr[i] == 2 * arr[j]`


```c++
class Solution {
public:
   bool checkIfExist(vector<int>& arr) {
        sort(arr.begin(), arr.end());
        for(int i=0; i<arr.size(); i++) {
            int low = 0;
            int high = arr.size() - 1;
            int target = 2 * arr[i];
            while(low <= high) {
                int mid = (low + high) / 2;
                if(arr[mid] == target && i != mid) return true;
                else if(arr[mid] < target) low = mid + 1;
                else high = mid - 1;
            }
        }
        return false;
    }
};
```
