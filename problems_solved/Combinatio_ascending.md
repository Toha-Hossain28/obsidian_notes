```c++
#include<bits/stdc++.h>
using namespace std;
int n,k;
//vector<int>A(n),B;

void Combination(vector<int>A,int idx,int r,vector<int>B){
    if(B.size()==r){
        for(int i=0;i<B.size()-1;i++){
            cout<<B[i]<<' ';
        }
        cout<<B[B.size()-1]<<endl;

        return;
    }
    if(idx==A.size()){
        return;
    }

    B.push_back(A[idx]);
    Combination(A,idx+1,r,B);
    B.pop_back();
    Combination(A,idx+1,r,B);
}

int main(){
    cin>>n>>k;
    vector<int>A(n);
    for(int i=0;i<n;i++){
        A[i]=n-i-1;
    }
    int indx=0;
    vector<int>B;
    Combination(A,indx,k,B);
}
```


```input
5 3
```


```output
4 3 2
4 3 1
4 3 0
4 2 1
4 2 0
4 1 0
3 2 1
3 2 0
3 1 0
2 1 0
```