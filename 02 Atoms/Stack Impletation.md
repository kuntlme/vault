---
tags:
  - atom
  - coding
Topics:
  - DSA
  - Stack
---
```cpp
#include <iostream>

#include <stack>

using namespace std;



class MyStack

{

public:

int *arr;

int size;

int top;



MyStack(int size)

{

this->size = size;

arr = new int(size);

top = -1;

}



void push(int element)

{

if (size - top > 1)

{

top++;

arr[top] = element;

}

else

{

cout << "stack overflowed" << endl;

}

}



void pop()

{

if (top == -1)

{

cout << "Stack Underflow" << endl;

}

else

{

top--;

}

}



int peak()

{

if (top >= 0 && top < size)

{

return arr[top];

}

else{

return -1;

}

}



bool isEmpty()

{

if (top == -1)

{

return true;

}

else

{

return false;

}

}

};



int main()

{

MyStack st(5);



st.push(5);



st.pop();



cout << st.peak() << endl;



cout << st.peak() << endl;



}
```
