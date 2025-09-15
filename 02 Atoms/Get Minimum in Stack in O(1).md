---
tags:
  - atom
  - coding
Topics:
  - DSA
  - Stack
---

# [155. Min Stack](https://leetcode.com/problems/min-stack/)

```cpp
class MinStack {
    stack<long long> s;
    long long mini = 0;
public:
    MinStack() {
    }

    void push(int val) {
        if(s.empty()){
            s.push(val);
            mini = val;
        }
        else{
            if(val < mini){
                long long ele = (val - mini) + val;
                s.push(ele);
                mini = val;
            }
            else{
                s.push(val);
            }
        }
    }

    void pop() {
        if(s.empty()){
            return;
        }
            long long curr = s.top();
            if(curr > mini){
                s.pop();
            }
            else{
                long long val = (mini - curr) + mini;
                mini = val;
                s.pop();
            }
    }

    int top() {
        if(s.empty()) return -1;
        if(s.top() < mini){
            return (int)mini;
        }
        else{
            return (int)s.top();
        }
    }

    int getMin() {
        if(s.empty()) return -1;
        return (int)mini;
    }
};

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack* obj = new MinStack();
 * obj->push(val);
 * obj->pop();
 * int param_3 = obj->top();
 * int param_4 = obj->getMin();
 */
```
