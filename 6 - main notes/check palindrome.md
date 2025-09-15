## Index: [[Recursion]]

`print true or false`

```c++
#include <iostream>

  

using namespace std;

  

void checkPalindrome(string input, int i){

int n = input.length();

if(i > n / 2){

cout << "true";

return;

}

if(input[i] != input[n - i - 1]){

cout << "false";

return;

}

checkPalindrome(input, i + 1);

}

  
  

int main() {

string input = "madam";

checkPalindrome(input, 0);

return 0;

}
```

`return ans`
```c++ 
#include <iostream>

  

using namespace std;

  

bool checkPalindrome(string input, int i){

int n = input.length();

if(i > n / 2){

return true;

}

if(input[i] != input[n - i - 1]){

return false;

}

return checkPalindrome(input, i + 1);

}

  
  

int main() {

string input = "madam";

bool ans = checkPalindrome(input, 0);

cout << ans;

return 0;

}
```
