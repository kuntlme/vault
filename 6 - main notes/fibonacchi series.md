## index: [[Recursion]]

`nth number`
```c++
#include <iostream>
using namespace std;

int fib(int num){

if(num == 1) return 0;

if(num == 2) return 1;

return fib(num - 1) + fib( num - 2);

}

  
  

int main() {

int num = 5;

int ans = fib(5);

cout << ans;

return 0;

}
```