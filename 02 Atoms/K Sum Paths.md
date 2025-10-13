---
tags:
  - atom
  - coding
Topics:
  - DSA
  - BTree
Reference Link: https://www.geeksforgeeks.org/problems/k-sum-paths/1
---
```cpp
/*
struct Node {
    int data;
    Node *left;
    Node *right;

    Node(int val) {
        data = val;
        left = right = NULL;
    }
};
*/
class Solution {
  public:
    void solve(Node* node, int k, int &count, vector<int>path){
        if(node == NULL) return;
        
        path.push_back(node -> data);
        solve(node -> left, k, count, path);
        solve(node -> right, k, count, path);
        
        int sum = 0;
        for(int i = path.size() - 1; i >= 0; i--){
            sum = sum + path[i];
            if(sum == k){
                count++;
            }
        } 
        path.pop_back();
    }
    int sumK(Node *root, int k) {
        int count = 0;
        vector<int> path;
        solve(root, k, count, path);
        return count;
    }
};
```