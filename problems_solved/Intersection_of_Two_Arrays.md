Given two integer arrays `nums1` and `nums2`, return _an array of their 

intersection

_. Each element in the result must be **unique** and you may return the result in **any order**.

```c++
class Solution {
public:
    bool BinSearch(vector<int>& vec, int n) {
        int start = 0;
        int end = vec.size()-1;
        while (start <= end) {
            int mid = (start + end) / 2;
            if (vec[mid] < n) {
                start = mid + 1;
            } else if (vec[mid] > n) {
                end = mid - 1;
            } else {
                return true;
            }
        }
        return false;
    }

    vector<int> intersection(vector<int>& nums1, vector<int>& nums2) {
        vector<int> res;
        sort(nums1.begin(), nums1.end());
        sort(nums2.begin(), nums2.end());
        for (int i = 0; i < nums1.size(); ++i) {
            // Avoid duplicates
            if (i > 0 && nums1[i] == nums1[i - 1]) {
                continue;
            }
            if (BinSearch(nums2, nums1[i])) {
                res.push_back(nums1[i]);
            }
        }
        return res;
    }
};
```
