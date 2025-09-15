---
tags:
  - atom
  - coding
Topics:
  - DSA
  - BTree
Reference Link: https://www.geeksforgeeks.org/problems/bottom-view-of-binary-tree/1
---
```cpp
/*
struct Node
{
    int data;
    Node* left;
    Node* right;
};
*/

class Solution {
  public:
    // Function to return a list of nodes visible from the top view
    // from left to right in Binary Tree.
    void solve(Node* node, int level, int depth, map<int, pair<int, int>> &levelEle){
        if(node == NULL) return;
        
        if(levelEle.find(level) == levelEle.end() || levelEle[level].second <= depth){
            levelEle[level] = {node -> data, depth};
        }
        
        solve(node -> left, level - 1, depth + 1, levelEle);
        solve(node -> right, level + 1, depth + 1, levelEle);
    }
    
    vector<int> bottomView(Node *root) {
        int level = 0;
        int depth = 0;
        map<int, pair<int, int>>levelEle;
        solve(root, level, depth, levelEle);
        vector<int> ans;
        for(auto i : levelEle){
            ans.push_back(i.second.first);
        }
        return ans;
        
    }
};
```