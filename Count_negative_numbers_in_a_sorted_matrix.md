[Count Negative Numbers in a Sorted Matrix](https://leetcode.com/problems/count-negative-numbers-in-a-sorted-matrix/)


Given a `m x n` matrix `grid` which is sorted in non-increasing order both row-wise and column-wise, return _the number of **negative** numbers in_ `grid`.

**Example 1:**

**Input:** grid =` [[4,3,2,-1],[3,2,1,-1],[1,1,-1,-2],[-1,-1,-2,-3]] `
**Output:** 8
**Explanation:** There are 8 negatives number in the matrix.

```c++
class Solution {

public:

int bin_search(vector<int> v, int col){

int low=0, high=col-1;

while(low<=high){

int mid=(low+high)/2;

if(v[mid]<0)high=mid-1;

else low=mid+1;

}

if(low>=col)return 0;

return col-low;

}

int countNegatives(vector<vector<int>>& grid) {

int r=grid.size();

int c=grid[0].size();

int i,j;

int neg_count=0;

for(i=0;i<r;i++){

neg_count+=bin_search(grid[i],c);

}

return neg_count;

}

};
```