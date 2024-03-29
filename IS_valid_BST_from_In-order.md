```c++
bool isValidBST(vector<int> &order){
     for (int i = 1; i < order.size(); ++i) {
        // Check if the current element is less than or equal to the previous element
        if (order[i] <= order[i - 1]) {
            return false;
        }
    }
    return true;
}

```