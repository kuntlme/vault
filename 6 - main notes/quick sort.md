```c++
#include <iostream>

#include <vector>

  

using namespace std;

  

void quickSort(vector<int>& arr, int s, int e){

if(s >= e){

return;

}

int pivot = s;

int i = s;

int j = e;

//check while arr[i] greater than pivot
//check while arr[j] less than pivot
// swap arr[i] and arr[j];
//repeat
//at last swap arr[pivot] and arr[j]

while(i < j){

while(arr[i] <= arr[pivot] && i < e){

i++;

}

while(arr[pivot] < arr[j] && j > s){

j--;

}

if(i < j)

swap(arr[i], arr[j]);

}

swap(arr[pivot], arr[j]);

quickSort(arr, s, j - 1);

quickSort(arr, j + 1, e);

}

  
  

int main() {

vector<int> arr = { 23, 6, 5, 35, 63, 12, 5, 6};

int n = arr.size();

quickSort(arr, 0, n - 1);

for(int i = 0; i < n; i++){

cout << arr[i] << " ";

}

return 0;

}
```

