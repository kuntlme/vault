## index: [[Recursion]]

```c++
#include <iostream>

#include<vector>

using namespace std;

  

void checkSum(vector<int>& arr, vector<int> ds, int index, int sum, int need){

if(index == arr.size()){

if(sum == need){

for(int i = 0; i < ds.size(); i++){

cout << ds[i] << " ";

}

cout << endl;

return;

}

return;

}

checkSum(arr, ds, index + 1, sum , need);

ds.push_back(arr[index]);

sum = sum + arr[index];

checkSum(arr, ds, index + 1, sum , need);

}

  

int main() {

vector<int> arr = {1,2,3,4,5};

vector<int> ds;

int sum = 5;

checkSum(arr, ds, 0, 0, sum);

}
```

`find only one subsequence of sum k`

```c++
#include <iostream>

#include<vector>

using namespace std;

  

bool checkSum(vector<int>& arr, vector<int>& ds, int index, int sum, int need){

if(sum == need){

return true;

}

if(index == arr.size()){

return false;

}

if(checkSum(arr, ds, index + 1, sum , need)){

return true;

}

ds.push_back(arr[index]);

sum = sum + arr[index];

if(checkSum(arr, ds, index + 1, sum , need)){

return true;

}

ds.pop_back();

return false;

}

  

int main() {

vector<int> arr = {1,5,1,6,3};

vector<int> ds;

int sum = 8;

bool ans = checkSum(arr, ds, 0, 0, sum);

if(ans){

for(int i = 0; i < ds.size(); i++){

cout << ds[i] << " ";

}

cout << endl;

}

return 0;

}
```

` count subsequences of sum k`

``` c++
#include <iostream>

#include<vector>

using namespace std;

  

int checkSum(vector<int>& arr, vector<int>& ds, int index, int sum, int need){

if(index == arr.size()){

if(sum == need){

return 1;

}

return 0;

}

int exclu = checkSum(arr, ds, index + 1, sum , need);

ds.push_back(arr[index]);

sum = sum + arr[index];

int inclu = checkSum(arr, ds, index + 1, sum , need);

ds.pop_back();

return exclu + inclu;

}

  

int main() {

vector<int> arr = {1,5,1,6,3};

vector<int> ds;

int sum = 7;

int ans = checkSum(arr, ds, 0, 0, sum);

cout << ans << endl;

return 0;

}
```

