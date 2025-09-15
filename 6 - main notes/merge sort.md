## index: [[Recursion]]

```c++
#include <iostream>

#include<vector>

using namespace std;

  

void merge(vector<int>& arr, int mid, int start, int end){

vector<int> ds;

int l = mid - start + 1;

int r = end - mid;

int k = 0;

int i = 0;

int j = 0;

while(i < l && j < r){

if(arr[start + i] <= arr[mid + 1 + j]){

ds.push_back(arr[start + i]);

i++;

k++;

}

else{

ds.push_back(arr[mid + 1 + j]);

j++;

k++;

}

}

while(i < l){

ds.push_back(arr[start + i]);

i++;

k++;

}

while(j < r){

ds.push_back(arr[mid + 1 + j]);

j++;

k++;

}

  

for(int m = 0; m < k; m++){

arr[start + m] = ds[m];

}

}

  
  

void mergeSort(vector<int>& arr, int start, int end){

if(start >= end){

return;

}

int mid = start + (end - start) / 2;

  

mergeSort(arr, start, mid);

mergeSort(arr, mid + 1, end);

merge(arr, mid, start, end);

}

  
  

int main() {

vector<int>arr = {1,24, 3, 53, 1, 65, 23, 5, 2, 9, 2};

int n = arr.size();

mergeSort(arr, 0, n - 1);

for(int i = 0; i < n; i++){

cout << arr[i] << " ";

}

return 0;

}
```