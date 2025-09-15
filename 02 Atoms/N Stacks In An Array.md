---
tags:
  - atom
  - coding
Topics:
  - DSA
  - Stack
---
## N Stacks In An Array
```cpp
#include <bits/stdc++.h> 
class NStack
{
public:
    int *arr;
    int *top;
    int *next;

    int freespot;
    int n, s;
    NStack(int N, int S)
    {
        n = N;
        s = S;
        arr = new int[s];
        next = new int[s];
        top = new int[n];

        // initialize the next
        for(int i = 0; i < s; i++){
            next[i] = i + 1;
        }

        // update the last next index to -1
        next[s-1] = -1;

        // initialize the top
        for(int i = 0; i < n; i++){
            top[i] = -1;
        }

        // initialize the freespot
        freespot = 0;
    }

    // Pushes 'X' into the Mth stack. Returns true if it gets pushed into the stack, and false otherwise.
    bool push(int x, int m)
    {

        if(freespot == -1){
            return false;
        }

        // find the index
        int index = freespot;

        // free spot update
        freespot = next[index];

        // insert in array
        arr[index] = x;
        
        // update next 
        next[index] = top[m - 1];

        // update top
        top[m - 1] = index;

        return true;
    }

    // Pops top element from Mth Stack. Returns -1 if the stack is empty, otherwise returns the popped element.
    int pop(int m)
    {
        if(top[m - 1] == -1){
            return -1;
        }

        int index = top[m - 1];

        top[m - 1] = next[index];

        next[index] = freespot;

        freespot = index;

        return arr[index];



    }
};
```