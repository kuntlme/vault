---
tags:
  - atom
  - coding
Topics:
  - DSA
  - Queue
Reference Link: https://www.geeksforgeeks.org/problems/first-negative-integer-in-every-window-of-size-k3345/1
---
```cpp
class Solution {
  public:
    vector<int> firstNegInt(vector<int>& arr, int k) {
        queue<int> q;
        vector<int> ans;

        // for first window
        for(int i = 0; i < k; i++){
            if(arr[i] < 0){
                q.push(i);
            }
        }

        if(!q.empty()){
            ans.push_back(arr[q.front()]);
        }
        else{
            ans.push_back(0);
        }

        for(int i = k; i < arr.size(); i++){
            if(!q.empty() && i - q.front() >= k){
                q.pop();
            }

            if(arr[i] < 0){
                q.push(i);
            }

            if(!q.empty()){
            ans.push_back(arr[q.front()]);
            }
            else{
                ans.push_back(0);
            }
        }

       return ans;
    }
};
```
