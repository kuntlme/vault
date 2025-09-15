## Index: [[Recursion]]

```c++
#include <iostream>

#include<vector>

using namespace std;

  

void printSS(vector<int>& arr, int n, vector<int> ds, int index){

if(index == n){

for(int i = 0; i < ds.size(); i++){

cout << ds[i] << " ";

}

cout << endl;

return;

}

printSS(arr, n, ds, index + 1);

ds.push_back(arr[index]);

printSS(arr, n, ds, index + 1);

}

  

int main() {

vector<int> arr = {1, 2, 3, 4, 5};

vector<int> ds;

int n = arr.size();

printSS(arr, n, ds, 0);

return 0;

}
```

