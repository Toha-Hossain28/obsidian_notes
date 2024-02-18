#sorting 
## C standard
```c++
#include<bits/stdc++.h>
using namespace std;

struct Node{
    int val;
    Node* next = nullptr;
};

int find_max(int arr[],int n){
    int max = arr[0];
    for(int i=1;i<n;i++){
        if(max<arr[i]){
            max = arr[i];
        }
    }
    return max;
}

void radix_sort(int arr[],int n){
    int max = find_max(arr,n);
    Node** ptr = new Node*[10];
    int div=0;
    while(div<max){
        for(int i=0;i<n;i++){
            int index = (arr[i]/div)%10;
            Node* a = new Node;
            a->val = arr[i];
            if(ptr[index]==nullptr){
                ptr[index]=a;
            }else{
                Node* p = ptr[index];
                while(p->next!=nullptr){
                    p = p->next;
                }
                p->next = a;
            }
        }
        div*=div;

        // Reconstruct the sorted array from buckets
        int j = 0;
        for (int i = 0; i <= max; i++) {
            Node* p = ptr[i];
            while (p != nullptr) {
                arr[j++] = p->val;
                Node* temp = p;
                p = p->next;
                delete temp; // Free memory
            }
        }
    }
    delete[] ptr;
}

int main(){
    int n;
    cin>>n;
    int arr[n];
    for(int i=0;i<n;i++){
        cin>>arr[i];
    }
    radix_sort(arr,n);
    for(int i=0;i<n;i++){
        cout<<arr[i]<<" ";
    }
    cout<<endl;
    return 0;
}
```