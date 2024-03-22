You are given an integer array numbs of length n, and an integer array queries of length m.

Return an array answer of length m where answer[i] is the maximum size of a sub-sequence that you can take from numbs such that the sum of its elements is less than or equal to queries[i].

```c++
class Solution {
public:
    // int BinSearch(vector<int>& vec, int n) {
    //     // int start = 0;
    //     int end = vec.size()-1;
    //     while (start <= end) {
    //         int mid = (start + end) / 2;
    //         if (vec[mid] < n) {
    //             start = mid + 1;
    //         } else if (vec[mid] > n) {
    //             end = mid - 1;
    //         } else {
    //             return ;
    //         }
    //     }
    //     return false;
    // }
    vector<int> answerQueries(vector<int>& nums, vector<int>& queries) {
        vector<int> ans;
        vector<int> sufsum(nums.size() + 1, 0); // Initialize sufsum with size and 0
        sort(nums.begin(), nums.end());
        for (int i = 0; i < nums.size(); i++) {
            sufsum[i + 1] = sufsum[i] + nums[i]; // Compute prefix sum
        }
        for (int i = 0; i < queries.size(); i++) {
            int count = 0;
            // Perform binary search to find the largest element in sufsum less than or equal to queries[i]
            count = upper_bound(sufsum.begin(), sufsum.end(), queries[i]) - sufsum.begin() - 1;
            ans.push_back(count);
        }
        return ans;
    }
};
```
