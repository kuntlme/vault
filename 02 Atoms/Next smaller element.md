---
tags:
  - atom
  - coding
Topics:
  - DSA
  - Stack
---
## Next smaller element

```cpp
#include<stack>
vector<int> nextSmallerElement(vector<int> &arr, int n)
{
    stack<int>st;
    vector<int>ans(n);
    st.push(-1);
    for(int i = n - 1; i >= 0; i--){
        int curr = arr[i];
        while(st.top() >= curr){
            st.pop();
        }
        ans[i] = st.top();
        st.push(curr);
    }
    return ans;


}
```
