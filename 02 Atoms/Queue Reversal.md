---
tags:
  - atom
  - coding
Topics:
  - DSA
Reference Link: https://www.geeksforgeeks.org/problems/queue-reversal/1
---
### Approach 1 -using stack
```cpp
// function Template for C++

class Solution {
  public:
    queue<int> reverseQueue(queue<int> &q) {
        stack<int> s;
        while(!q.empty()){
            s.push(q.front());
            q.pop();
        }
        while(!s.empty()){
            q.push(s.top());
            s.pop();
        }
        return q;
    }
};
```

### Appraoch 2 - using recursion

```cpp
// function Template for C++

class Solution {
  public:
    void solve(queue<int> &q){
                if(q.empty()){
            return;
        }
        
        int ele = q.front();
        q.pop();
        solve(q);
        q.push(ele);
    }
    queue<int> reverseQueue(queue<int> &q) {
        solve(q);
        return q;
    }
};
```
