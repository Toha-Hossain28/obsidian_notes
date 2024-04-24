```c++
#include <bits/stdc++.h>
#define ll long long
#define endl '\n'
#define vll vector<long long>
#define vi vector<int>
#define vp vector<pair<int, int>>
using namespace std;
vector<char>ans;
string s;
int n;
void f(int pos){
    if(pos==n){
        for(int i=0;i<n;i++){
            cout<<ans[i];
        }
        cout<<endl;
        return;
    }
    for(int i=0;i<n;i++){
        char ch=s[i];
        bool ok=true;
        for(int j=0;j<ans.size();j++){
            if(ans[j]==ch){
                ok=false;
                break;
            }
            
        }
        if(ok){
            ans.push_back(ch);
            //ans[pos]=ch;
            f(pos+1);
            ans.pop_back();
        }
    }

}

void CODE_PARI_NA(){
    cin>>n;
    cin>>s;
    f(0);
}
int32_t main(){
    ios_base::sync_with_stdio(0);
    cin.tie(0);
    cout.tie(0);
    int t = 1;
    // cin >> t;
    while (t--){
       CODE_PARI_NA();
    }
    return 0;
}
```

```input
3
abc
```

```output
abc
acb
bac
bca
cab
cba
```
