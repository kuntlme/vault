### Index: [[Recursion]]

`paramerter recursion`

``` c++
#include <iostream>

using namespace std;

int firstsum(int n, int sum){

	if(n == 0) {
	
		return sum;
	
	}
	
	sum = sum + n;
	
	return firstsum(n - 1, sum);

}

  

int main() {

	int ans = firstsum(10);
	
	cout << ans;
	
	return 0;

}
```


`functional recursion`

``` c++
#include <iostream>

using namespace std;

int firstsum(int n){

	if(n == 0) {
	
		return 0;
	
	}
	return n + firstsum(n - 1);
}

  

int main() {

	int ans = firstsum(10);
	
	cout << ans;
	
	return 0;

}
```

