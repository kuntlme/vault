```c++
#include <iostream>

#include<vector>

using namespace std;



void pairSum(vector < int > & arr, vector < vector < int >> & ans, vector < int > ds, int target, int sum, int index) {

    if (sum == target) {

        ans.push_back(ds);

        return;

    }



    if (sum < target && index < arr.size()) {

        pairSum(arr, ans, ds, target, sum, index + 1);

        sum = arr[index] + sum;

        ds.push_back(arr[index]);

        pairSum(arr, ans, ds, target, sum, index + 1);

    }

}



int main() {

    vector < int > arr = {
        1,
        3,
        5,
        2,
        5,
        6,
        6,
        3,
        6,
        7,
        5,
        2
    };

    int target = 12;

    vector < int > ds;

    vector < vector < int >> ans;

    pairSum(arr, ans, ds, target, 0, 0);

    for (int i = 0; i < ans.size(); i++) {

        for (int j = 0; j < ans[i].size(); j++) {

            cout << ans[i][j] << " ";

        }

        cout << endl;

    }

    return 0;

}
```

