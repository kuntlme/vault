---
tags:
  - atom
  - coding
Topics:
  - DSA
  - BTree
Reference Link: https://www.geeksforgeeks.org/problems/count-leaves-in-binary-tree/1
---
```cpp
/* A binary tree node has data, pointer to left child
   and a pointer to right child
struct Node
{
    int data;
    Node* left;
    Node* right;
}; */

// Class Solution
class Solution {
  public:
    void solve(Node* &root, int &count){
        if(root == NULL) return;
        
        if(root -> left == NULL && root -> right == NULL) count++;
        solve(root -> left, count);
        solve(root -> right, count);
    }
    int countLeaves(Node* root) {
        int count = 0;
        solve(root, count);
        return count;
        
    }
};
```