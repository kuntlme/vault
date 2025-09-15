---
tags:
  - atom
  - coding
Topics:
  - DSA
  - Queue
Reference Link: https://www.geeksforgeeks.org/problems/reverse-first-k-elements-of-queue/1
---
```cpp
#include<stack>
class Solution {
  public:
    queue<int> reverseFirstK(queue<int> q, int k) {
        stack<int> s;
        int n = q.size();
        int rev = n - k;
        if(rev < 0) return q;
        for(int i = 0; i < k; i++){
            int ele = q.front();
            q.pop();
            s.push(ele);
        }
        while(!s.empty()){
            int ele = s.top();
            s.pop();
            q.push(ele);
        }

        int i = 0;
        while(i < rev){
            int ele = q.front();
            q.pop();
            q.push(ele);
            i++;
        }
        
        return q;
    }
};
```
