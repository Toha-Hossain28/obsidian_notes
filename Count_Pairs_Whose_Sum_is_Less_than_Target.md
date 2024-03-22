Given a **0-indexed** integer array `nums` of length `n` and an integer `target`, return _the number of pairs_ `(i, j)` _where_ `0 <= i < j < n` _and_ `nums[i] + nums[j] < target`.

**Example 1:**

**Input:** nums = [-1,1,2,3,1], target = 2
**Output:** 3
**Explanation:** There are 3 pairs of indices that satisfy the conditions in the statement:
- (0, 1) since 0 < 1 and nums[0] + nums[1] = 0 < target
- (0, 2) since 0 < 2 and nums[0] + nums[2] = 1 < target 
- (0, 4) since 0 < 4 and nums[0] + nums[4] = 0 < target
Note that (0, 3) is not counted since nums[0] + nums[3] is not strictly less than the target.

```c++
class Solution {

public:

int countPairs(vector<int>& nums, int target) {

sort(nums.begin(),nums.end());

int pairCount=0;

int left=0;

int right = nums.size()-1;

while(left<right)

{

if(nums[left]+nums[right]<target)

{

pairCount += right-left;

left++;

}

else{

right--;

}

}

return pairCount;

}

};
```