```c++
#include<bits/stdc++.h>
using namespace std;
int n;
vector<int>a;
void f(int pos){
    if(pos==n){
        for(int i=0;i<n-1;i++){
            cout<<a[i]<<' ';
        }
        cout<<a[n-1];
        cout<<endl;
        return;
    }
    for(int i=4;i>=0;i--){
        if(pos%2==i%2) continue;
        a.push_back(i);
        f(pos+1);
        a.pop_back();
    }
}
int main(){
    cin>>n;
    f(0);
}
```

```input
3
```
```output
3 4 3
3 4 1
3 2 3
3 2 1
3 0 3
3 0 1
1 4 3
1 4 1
1 2 3
1 2 1
1 0 3
1 0 1
```
