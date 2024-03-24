```c++
class Solution{
    public:
    // arr: input array
    // n: size of array
    //Function to find the sum of contiguous subarray with maximum sum.
    long long maxSubarraySum(int arr[], int n) {
        long long max_sum = arr[0];
        long long max_till_now = arr[0];
        for(int i = 1; i < n; i++) {
            max_till_now = max((long long)arr[i], max_till_now + arr[i]);
            max_sum = max(max_sum, max_till_now);
        }
        return max_sum;
    }
};
```
