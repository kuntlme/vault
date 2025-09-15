---
tags:
  - atom
  - coding
Topics:
  - DSA
  - BTree
Reference Link: https://www.geeksforgeeks.org/problems/top-view-of-binary-tree/1
---
```cpp/*
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
    void solve(Node* node, int level, map<int, int> &levelEle){
        if(node == NULL) return;
        
        //level not exist
        if(levelEle.find(level) == levelEle.end()){
            levelEle[level] = node -> data;
        }
        
        solve(node -> left, level - 1, levelEle);
        solve(node -> right, level + 1, levelEle);

    }
    vector<int> topView(Node *root) {
        int level = 0;
        map<int, int>levelEle;
        solve(root, level, levelEle);
        vector<int> ans;
        for(auto i : levelEle){
            ans.push_back(i.second);
        }
        return ans;
        
    }
};

```