![[Pasted image 20240511155514.png]]

![[Pasted image 20240511155646.png]]

![[Pasted image 20240511155904.png]]

```c++
#include<bits/stdc++.h>
using namespace std;

int parent[100000];
int r[100000];

int find_set(int v)
{
    if(v == parent[v])
    {
        return v;
    }
    else
    {
        return parent[v] = find_set(parent[v]);
    }
}

int find(int i,int j)
{
    int root_of_i = find_set(i);
    int root_of_j = find_set(j);

    if(root_of_i == root_of_j)
    {
        return 1;
    }
    else
    {
        return 0;
    }
}

void union_set(int i, int j){
    int root_of_i = find_set(i);
    int root_of_j = find_set(j);

    if(root_of_i == root_of_j)
    {
        return;
    }
    if( r[root_of_i] < r[root_of_j])
    {
        parent[root_of_i] = root_of_j;
    }
    else 
    {
        parent[root_of_j] = root_of_i;
        if(r[root_of_i] == r[root_of_j])
        {
            r[root_of_i]++;
        }
    }
}

int main()
{
    for(int i=0;i<100000;i++)
    {
        parent[i] = i;
        r[i] = 0;
    }
    cout<<find(1,2)<<endl;
    union_set(1,2);
    cout<<find(1,2)<<endl;
    union_set(2,3);
    cout<<find(1,3)<<endl;

    return 0;
}
```