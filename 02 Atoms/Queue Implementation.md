---
tags:
  - atom
  - coding
Topics:
  - DSA
  - Queue
Reference Link: https://www.naukri.com/code360/problems/queue-using-array-or-singly-linked-list_2099908?leftPanelTabValue=SUBMISSION
---
```cpp

#include <bits/stdc++.h> 
class Queue {
    int *arr;
    int frontE;
    int rear;
    int size;
public:
    Queue() {
        size = 1000001;
        arr = new int[size];
        frontE = 0;
        rear = 0;
    }

    /*----------------- Public Functions of Queue -----------------*/

    bool isEmpty() {
        return rear == frontE;
    }

    void enqueue(int data) {
        if(rear == size) return;
        arr[rear] = data;
        rear++;
    }

    int dequeue() {
        if(frontE == rear) return -1;
        int ele = arr[frontE];
        frontE++;
        if(frontE == rear){
            frontE = 0;
            rear = 0;
        }
        return ele;

    }

    int front() {
        if(frontE == rear) return -1;
        return arr[frontE];
    }
};
```