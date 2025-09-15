---
tags:
  - atom
  - coding
Topics:
  - DSA
  - Queue
---
```cpp
class MyCircularQueue {
    int *arr;
    int size;
    int rear;
    int front;
public:
    MyCircularQueue(int k) {
        size = k;
        arr = new int[size];
        rear = -1;
        front = -1;
    }
    
    bool enQueue(int value) {
        // check full
        if(isFull()){
            return false;
        }
        // first ele
        else if(front == -1){
            rear = 0;
            front = 0;
            arr[rear] = value;
        }
        else if(rear == size - 1 && front  != 0){
            rear = 0;
            arr[rear] = value;
        }
        else{
            rear++;
            arr[rear] = value;
        }
        return true;

    }
    
    bool deQueue() {
        if(front == -1){
            return false;
        }
        //single elemenet
        else if(rear == front){
            front = -1;
            rear = -1;
        }
        else if(front == size - 1){
            front = 0;
        }
        else{
            front++;
        }

        return true;
    }
    
    int Front() {
        if(front == -1 ) return -1;
        return arr[front];
    }
    
    int Rear() {
        if(rear == -1) return -1;
        return arr[rear];
    }
    
    bool isEmpty() {
        if(front == -1) return true;
        return false;
    }
    
    bool isFull() {
        return (rear + 1) % size == front;
    }
};

/**
 * Your MyCircularQueue object will be instantiated and called as such:
 * MyCircularQueue* obj = new MyCircularQueue(k);
 * bool param_1 = obj->enQueue(value);
 * bool param_2 = obj->deQueue();
 * int param_3 = obj->Front();
 * int param_4 = obj->Rear();
 * bool param_5 = obj->isEmpty();
 * bool param_6 = obj->isFull();
 */
```