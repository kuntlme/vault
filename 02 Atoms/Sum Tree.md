---
tags:
  - atom
  - coding
Topics:
  - DSA
  - BTree
Reference Link: https://www.geeksforgeeks.org/problems/sum-tree/1
---
```cpp
/*  Tree node
struct Node
{
    int data;
    Node* left, * right;
}; */

// Should return true if tree is Sum Tree, else false
class Solution {
  public:
   int solve(Node* node, bool &check){
        if(node == NULL) return 0;
        if(node -> left == NULL && node -> right == NULL) return node -> data;

        int leftSum = solve(node -> left, check);
        int rightSum = solve(node -> right, check);
        

        if(node -> data != (leftSum + rightSum)){
            check = false;
        }
        return leftSum + rightSum + node -> data;
    }
    bool isSumTree(Node* root) {
        bool check = true;
        int sum = solve(root, check);
        return check;
        
    }
};
```