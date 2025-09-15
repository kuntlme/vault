---
tags:
  - atom
  - coding
Topics:
  - DSA
  - BTree
Reference Link: https://www.geeksforgeeks.org/problems/boundary-traversal-of-binary-tree/1
---
```cpp
class Solution {
  public:
  
    void traverseLeft(Node *node, vector<int> &ans){
        if(node == NULL || (node->left == NULL && node->right == NULL)) return;
        
        ans.push_back(node->data);
        
        if(node->left){
            traverseLeft(node->left, ans);
        }
        else{
            traverseLeft(node->right, ans);
        }
    }
    
    void traverseLeaf(Node *node, vector<int> &ans){
        if(node == NULL) return;
        
        if(node->left == NULL && node->right == NULL){ 
            ans.push_back(node->data);
            return;
        }
        
        traverseLeaf(node->left, ans);
        traverseLeaf(node->right, ans);
    }
    
    void traverseRight(Node *node, vector<int> &ans){
        if(node == NULL || (node->left == NULL && node->right == NULL)) return;
        
        if(node->right){
            traverseRight(node->right, ans);
        }
        else{
            traverseRight(node->left, ans);
        }
        
        ans.push_back(node->data); // add after child for reverse order
    }
    
    vector<int> boundaryTraversal(Node *root) {
        vector<int> ans;
        if(root == NULL) return ans;
        
        ans.push_back(root->data);  // root first
        
        traverseLeft(root->left, ans);
        
        traverseLeaf(root->left, ans);
        traverseLeaf(root->right, ans);
        
        traverseRight(root->right, ans);
        
        return ans;
    }
};

```