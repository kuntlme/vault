---
tags:
  - atom
  - coding
Topics:
  - DSA
  - BTree
Reference Link: https://www.geeksforgeeks.org/problems/left-view-of-binary-tree/1
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
    // Function to return a list of nodes visible from the top view
    // from left to right in Binary Tree.
    void solve(Node* node, int depth, map<int, int> &levelEle){
        if(node == NULL) return;
        
        if(levelEle.find(depth) == levelEle.end()){
            levelEle[depth] = node -> data;
        }
        
        solve(node -> left, depth + 1, levelEle);
        solve(node -> right, depth + 1, levelEle);
    }
    
    vector<int> leftView(Node *root) {
        int depth = 0;
        map<int, int>levelEle;
        solve(root, depth, levelEle);
        vector<int> ans;
        for(auto i : levelEle){
            ans.push_back(i.second);
        }
        return ans;
        
    }
};
```