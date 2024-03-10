#DSA #sorting 

```c++
#include<bits/stdc++.h>
using namespace std;

void merge(int arr[], int low, int high)
{
	int mid = (high + low) / 2;
	int i = low;
	int j = mid + 1;
	int k = 0;
	int B[high - low + 1];
	while(i <= mid && j <= high)
	{
		if(arr[i] < arr[j])
		{
			B[k++] = arr[i++];
		}
		else
		{
			B[k++] = arr[j++];
		}
	}
	while(i <= mid)
	{
		B[k++] = arr[i++];
	}
	while(j <= high)
	{
		B[k++] = arr[j++];
	}
	for (int p = low; p <= high; p++) // Corrected the loop index from i to p
	{
		arr[p] = B[p - low]; // Adjusted index to copy elements correctly
	}
}

  
  

void mergeSort(int arr[], int low, int high)
{
	int mid;
	if(low<high)
	{
		mid = (low + high) / 2;
		mergeSort(arr, low, mid);
		mergeSort(arr, mid + 1, high);
		merge(arr, low, high);
	}
}

  

int main(){
	int arr[10]={10,9,8,7,6,5,4,3,2,1};
	mergeSort(arr, 0, 9);
	for(auto x: arr){
		cout << x << endl;
	}
	return 0;
}
```