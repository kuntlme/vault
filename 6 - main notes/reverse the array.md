## Index: [[Recursion]]

`print in reverse`

``` c++
#include <iostream>

#include <vector>

  

using namespace std;

  

void printReverseArr(vector<int>& arr, int n, int i){

if(i == n){

return;

}

printReverseArr(arr, n, i + 1);

cout << arr[i] << " ";

}

  
  

int main() {

vector<int>arr = {1, 2, 3, 4};

int n = arr.size();

printReverseArr(arr, n, 0);

return 0;

}

```


`reverse the array`


``` c++
#include <iostream>

#include <vector>

  

using namespace std;

  

void reverseArr(vector<int>& arr, int n, int i){

if(i > n / 2){

return;

}

swap(arr[i], arr[n - i - 1]);

reverseArr(arr, n, i + 1);

}

  
  

int main() {

vector<int>arr = {1, 2, 3, 4, 5};

int n = arr.size();

reverseArr(arr, n, 0);

for(int i = 0; i < n; i++){

cout << arr[i] << " ";

}

return 0;

}****

```
