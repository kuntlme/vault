---
tags:
  - atom
  - coding
Topics:
  - DSA
  - BTree
Reference Link: https://www.geeksforgeeks.org/problems/lowest-common-ancestor-in-a-binary-tree/1
---
```cpp
/*
class Node {
public:
    int data;
    Node* left;
    Node* right;

    Node() {
        data = 0;
        left = right = NULL;
    }

    Node(int x) {
        data = x;
        left = right = NULL;
    }
};
 */

class Solution {
  public:
    Node* lca(Node* root, int n1, int n2) {
        if(root == NULL) return NULL;
        
        if(root -> data == n1 || root -> data == n2){
            return root;
        }
        
        Node* left = lca(root -> left, n1, n2);
        Node* right = lca(root -> right, n1, n2);
        if(left != NULL && right != NULL) return root;
        else if(left != NULL && right == NULL){
            return left;
        }
        else if(right != NULL && left == NULL){
            return right;
        }
        else {
            return NULL;
        }
        
    }
};
```