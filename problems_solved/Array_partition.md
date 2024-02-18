#DSA #sorting #leetcode

```c++
class Solution {
public:
    int arrayPairSum(vector<int>& nums) {
        int m[2*10001] = {0};
        int n = nums.size();

        int max_val = nums[0];
        for (int i = 0; i < n; i++) {
            if (nums[i] > max_val) {
                max_val = nums[i];
            }
        }

        int min_val = nums[0];
        for (int i = 0; i < n; i++) {
            if (nums[i] < min_val) {
                min_val = nums[i];
            }
        }
        int range;
        if(min_val<0) range = max_val - min_val + 1;
        else range = max_val;

        if (min_val > -1) {
            for (int i = 0; i < n; i++) {
                m[nums[i]]++;
            }
        } else {
            for (int i = 0; i < n; i++) {
                m[nums[i] + abs(min_val)]++;
            }
        }
        vector<int> res;
        for (int i = 0; i <= range;) {
            if(min_val>-1){
                if (m[i] == 0) {
                    i++;
                } else {
                    res.push_back(i);
                    m[i]--;
                }
            }
            else{
                if (m[i] == 0) {
                    i++;
                } else {
                    int z = i + min_val;
                    res.push_back(z);
                    m[i]--;
                }
            }
            
        }
        int x = 0;
        for (int i = 0; i < n; i += 2) {
            x += res[i];
        }
        return x;
    }
};
```