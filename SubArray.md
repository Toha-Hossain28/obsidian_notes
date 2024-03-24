```c++
#include<iostream>
using namespace std;

void power_set(string s,int i,string &curr){
    if(i==s.length()){
        cout<<curr<<"\n";
        return;
    }
    curr+=s[i];
    power_set(s,i+1,curr);
    curr.pop_back();
    power_set(s,i+1,curr);
}
int main(){

    string s;
    cin>>s;
    string curr;
    power_set(s,0,curr);
    return 0;
}
```
