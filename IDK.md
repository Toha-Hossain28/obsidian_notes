```c++
#include <bits/stdc++.h>
#define ll long long
#define endl '\n'
#define vll vector<long long>
#define vi vector<int>
#define vp vector<pair<int, int>>
using namespace std;
int n;
int a[20];
bool is_taken[20];
void rec(int pos){
    if(pos>n){
        for(int i=1;i<=n;i++){
            if(is_taken[i]){
                cout<<a[i]<<' ';
            }
        }
        cout<<endl;
        return;
    }
    is_taken[pos]=false;
    rec(pos+1);
    is_taken[pos]=true;
    rec(pos+1);
}

void CODE_PARI_NA(){
    cin>>n;
    for(int i=1;i<=n;i++){
        cin>>a[i];
    }
    rec(1);
}
int32_t main(){
    ios_base::sync_with_stdio(0);
    cin.tie(0);
    cout.tie(0);
    CODE_PARI_NA();
    return 0;
}
```

```input
3
5 6 7
```

```output
7 
6 
6 7 
5 
5 7 
5 6 
5 6 7 
```