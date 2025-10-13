---
tags:
  - atom
  - coding
Topics:
  - DSA
  - BTree
Reference Link: https://www.geeksforgeeks.org/problems/maximum-sum-of-non-adjacent-nodes/1
---
```cpp
/*
class Node {
public:
    int data;
    Node* left;
    Node* right;
    Node(int val) {
        data = val;
        left = nullptr;
        right = nullptr;
    }
};
*/

class Solution {
  public:
    pair<int, int>solve(Node* node){
        // base case 
        if(node == NULL){
            pair<int, int> temp = {0, 0};
            return temp;
        }
        
        pair<int, int> leftPair = solve(node -> left);
        pair<int, int> rightPair = solve(node -> right);
        
        pair<int, int> temp;
        //include
        temp.first = leftPair.second + rightPair.second + node -> data;
        // exclude
        temp.second = max(leftPair.first, leftPair.second) + max(rightPair.first, rightPair.second);
        return temp;
    }
    int getMaxSum(Node *root) {
        pair<int, int> ans = solve(root);
        // cout << ans.first << " " << ans.second << endl;
        return max(ans.first, ans.second);
    }
};
```