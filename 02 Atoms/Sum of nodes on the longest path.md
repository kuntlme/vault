---
tags:
  - atom
  - coding
Topics:
  - DSA
  - BTree
Reference Link: http://geeksforgeeks.org/problems/sum-of-the-longest-bloodline-of-a-tree/1
---
```cpp
/*
class Node {
  public:
    int data;
    Node *left;
    Node *right;

    Node(int x) {
        data = x;
        left = NULL;
        right = NULL;
    }
}; */

class Solution {
  public:
    void solve(Node *node, int &maxSum, int &maxLen, int len, int sum){
        if(node == NULL){
            //length same
            if(len == maxLen){
                // sum greater
                if(maxSum < sum ){
                    maxSum = sum;
                }
                return;
            }
            if(len > maxLen){
                maxLen = len;
                maxSum = sum;
                return;
            }
            else{
                return;
            }
        }
        
        solve(node -> left, maxSum, maxLen, len + 1, sum + node -> data);
        solve(node -> right, maxSum, maxLen, len + 1, sum + node -> data);
        
    }
    int sumOfLongRootToLeafPath(Node *root) {
        int maxSum = 0;
        int maxLen = 0;
        int len = 0;
        int sum = 0;
        solve(root, maxSum, maxLen, len, sum);
        return maxSum;
        
    }
};
```