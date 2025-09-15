---
tags:
  - molecule
  - coding
Topics:
  - DSA
  - Stack
---
### tags: #coding #dsa

[[Stack Impletation]]

## Remove middle

```cpp
#include <iostream>
#include <stack>
using namespace std;

void solve(stack<int> &st, int count, int size)
{
    // base case
    if (count == size / 2)
    {
        st.pop();
        return;
    }

    int ele = st.top();
    st.pop();

    // recursive
    solve(st, count+1, size);

    st.push(ele);
    return;
}

void removeMiddle(stack<int> &st, int size)
{
    int count = 0;
    solve(st, count, size);
}

int main()
{
    stack<int> st;
    int size = 5;
    int input[] = {1, 2, 3, 4, 5};
    for (int i = 0; i < size; i++)
    {
        st.push(input[i]);
        cout << st.top() << " ";
    }
    cout << endl;
    removeMiddle(st, size);
    for (int i = 0; i < size - 1; i++)
    {
        int ele = st.top();
        cout << ele << " ";
        st.pop();
    }
}
```

## valid parenthisis

```cpp
else{
class Solution {
public:
    bool isValid(string s) {
        stack<char> st;
        int i = 0;
        while(i < s.length()){
            if(s[i] == '(' || s[i] == '{' || s[i] == '['){
                st.push(s[i]);
            }
            else{
                if(s[i] == ')'){
                    if(st.empty() == 0 && st.top() == '(') st.pop();
                    else return false;

                }
                else if(s[i] == ']'){
                    if(st.empty() == 0 && st.top() == '[') st.pop();
                    else return false;
                }
                else{
                    if(st.empty() == 0 && st.top() == '{') st.pop();
                    else return false;
                }
            }
            i++;
        }
        if(st.empty()){
            return true;

        }
        else{
            return false;
        }
    }
};

```

## Insert at the bottom of the stack

```cpp
#include <iostream>
#include <stack>
using namespace std;

void insert(stack<int> &st, int data)
{
    if(st.empty()){
        st.push(data);
        return;
    }

    int ele = st.top();
    st.pop();
    insert(st, data);
    st.push(ele);
}

void inserBottom(stack<int> &st, int data)
{
    insert(st, data);
}

int main()
{
    stack<int> st;
    int size = 6;
    int data = 77;
    int input[] = {1, 2, 3, 4, 5, 6};
    for (int i = 0; i < size; i++)
    {
        st.push(input[i]);
        cout << st.top() << " ";
    }
    cout << endl;
    inserBottom(st, data);
    for (int i = 0; i < size + 1; i++)
    {
        int ele = st.top();
        cout << ele << " ";
        st.pop();
    }
}
```

## Redundant Brackets

```c++
#include <bits/stdc++.h>
#include<stack>
bool findRedundantBrackets(string &s)
{
    stack<char> st;
    for(int i = 0; i < s.length(); i++){
        if(s[i] == '(' || s[i] == '+' || s[i] == '-' || s[i] == '*' || s[i] == '/' ){
            st.push(s[i]);
        }
        else{
                if(s[i] == ')'){
                bool isRedundant = true;
                while(st.top() != '('){
                    if(st.top() == '+' || st.top() == '-' || st.top() == '*' || st.top() == '/' ){
                        isRedundant = false;
                    }
                    st.pop();
                }
                if(isRedundant){
                    return true;
                }
                st.pop();
            }
        }
    }
    return false;
}

```

## Minimum Cost To Make String Valid / Minimum Brackets Reversal

```cpp
#include<stack>
#include <bits/stdc++.h>
int findMinimumCost(string str) {
  if(str.length() % 2 == 1){
    return -1;
  }

  stack<char> st;
  for(int i = 0; i < str.length(); i++){
    if(str[i] == '{'){
      st.push(str[i]);
    }
    else{
      if(str[i] == '}'){
        if(!st.empty() && st.top() == '{'){
          st.pop();
        }
        else{
          st.push(str[i]);
        }
      }
    }
  }

  int a = 0;
  int b = 0;
  while(st.empty() != 1){
    if(st.top() == '{'){
      a++;
      st.pop();
    }
    else{
      b++;
      st.pop();
    }
  }

  return ((a + 1) / 2) + ((b + 1) / 2);
}
```

[[Next smaller element]]
[[84. Largest Rectangle in Histogram]]
[[The Celebrity Problem]]
[[85. Maximal Rectangle]]
[[N Stacks In An Array]]
[[Get Minimum in Stack in O(1)]]

---

**Question 1: Reverse String Using Stack**

- **Problem:** To reverse a given string utilizing a stack data structure, contrasting with prior methods like element swapping.
- **Approach:** Leverages the **Last-In, First-Out (LIFO)** property of a stack.
    - Each character from the input string is **pushed** onto the stack.
    - Subsequently, characters are **popped** from the stack sequentially.
    - These popped characters form the reversed string.
- **Complexity:**
    - **Time Complexity:** O(N), where N is the number of characters in the string.
    - **Space Complexity:** O(N).

---

**Question 2: Delete Middle Element From Stack**

- **Problem:** To remove the middle element from a given stack.
- **Approach:** Solved using **recursion**.
    - Elements are **popped** from the stack and temporarily stored.
    - A recursive call is made to process the remaining stack.
    - The **base case** is triggered when the "middle" element is reached, determined by `size/2`.
    - Once the middle element is identified, it is **popped** and discarded.
    - Upon the return of recursive calls, the temporarily stored elements are **pushed back** onto the stack in their original order.

---

**Question 3: Evaluate Parentheses / Valid Parentheses**

- **Problem:** To ascertain if an expression containing parentheses is "valid" or "balanced". A valid expression requires each opening bracket to have a corresponding closing bracket in the correct form (e.g., `()` or `([{}])` are balanced, while `([)]` is not).
- **Approach:** A stack is used to track opening brackets. The expression is iterated character by character:
    - **Opening brackets** (`(`, `[`, `{`) are **pushed** onto the stack.
    - **Closing brackets** (`)`, `]`, `}`) trigger a check: If the stack is not empty and its top element is the **corresponding opening bracket**, then both are a match, and the opening bracket is **popped**.
    - If the stack is empty or the top element does not match the closing bracket, the expression is deemed **invalid**.
- **Result:** The expression is **valid** if the stack is **empty** at the end of the iteration; otherwise, it is invalid.
- **Complexity:**
    - **Time Complexity:** O(N), where N is the length of the expression.

---

**Question 4: Insert an Element at the Bottom in a Given Stack**

- **Problem:** To insert a new element at the very bottom of an existing stack.
- **Approach:** Solved using **recursion**.
    - Elements are **popped** from the stack one by one until the stack becomes **empty**.
    - When the stack is empty, the new element is **pushed** onto it (making it the bottom element).
    - Subsequently, the previously popped elements are **pushed back** onto the stack in their original order.

---

**Question 5: Reverse Stack Using Recursion**

- **Problem:** To reverse the entire stack using **recursion**.
- **Approach:** This method integrates the logic from "deleting" and "inserting at bottom" problems.
    - The top element is **popped** and temporarily saved.
    - A **recursive call** is then made to **reverse the remaining stack**.
    - Once the recursive call returns (implying the rest of the stack is now reversed), the saved element is then **inserted at the bottom** of the now-reversed stack, using the "Insert at Bottom" logic.
- **Complexity:**
    - **Time Complexity:** O(N).

---

**Question 6: Sort Stack**

- **Problem:** To sort the elements in a stack in **increasing order**.
- **Approach:** Achieved using **recursion** and a helper function called **"Insert Sorted"**.
    - An element is **popped** from the stack.
    - A **recursive call** is made to **sort the remaining stack**.
    - Once the recursive call returns, the popped element is then **inserted in a sorted manner** into the now-sorted stack using the "Insert Sorted" helper function.
- **"Insert Sorted" Helper Function:** This function inserts an element into an already sorted stack while maintaining order. It recursively pops elements until it finds a position where the new element can be pushed without violating sorted order (either the stack becomes empty or the top element is smaller than the new element). Previously popped elements are then pushed back.
- **Complexity:**
    - **Time Complexity:** O(N^2).

---

**Question 7: Redundant Brackets**

- **Problem:** To determine if an arithmetic expression contains any **"redundant" or "unnecessary" brackets**. A bracket is redundant if its sub-expression could be evaluated without it (e.g., `((a+b))` has redundant outer brackets because `(a+b)` is sufficient).
- **Approach:** A stack is used to process the expression.
    - **Opening brackets** (`(`, `[`, `{`) and **operators** (`+`, `-`, `*`, `/`) are **pushed** onto the stack.
    - When a **closing bracket** is encountered, elements are **popped** from the stack until the corresponding opening bracket is found. The objective is to check for an operator between the corresponding opening and closing brackets.
    - **If an operator is found** during this popping process, the brackets are **not redundant** (they enclosed an operation). A flag can be set to `false` for redundancy.
    - **If no operator is found** (meaning only the opening bracket was immediately popped), the brackets are **redundant**. In this case, the function can immediately return `true`.
    - The corresponding opening bracket is then popped.
- **Complexity:**
    - **Time Complexity:** O(N).

---

**Question 8: Minimum Cost To Make String Valid / Minimum Brackets Reversal**

- **Problem:** Given a string of only curly braces (`{`, `}`), find the **minimum number of reversals needed to make the string valid**. A valid string has matching opening and closing braces.
- **Edge Case:** If the **total length of the string is odd**, it's **impossible** to make it valid, so **-1 is returned**.
- **Approach:**
    1.  **Remove Valid Pairs:** A stack is used. Any opening brace is pushed. If a closing brace is encountered and the stack top is an opening brace, they form a valid pair, and the opening brace is popped. If a closing brace is encountered and the stack top is not an opening brace (or stack is empty), it is pushed onto the stack as it's unmatched.
    2.  **Count Unmatched Braces:** After processing, the remaining stack elements represent the "invalid" part. This remaining part will consist of unmatched closing braces (`b`) followed by unmatched opening braces (`a`) (e.g., `}}{{{`).
    3.  **Calculate Reversals:** The minimum reversals are calculated using the formula: **`(a + 1) / 2 + (b + 1) / 2`**.
- **Complexity:**
    - **Time Complexity:** O(N).
