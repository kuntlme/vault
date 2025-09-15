---
tags:
  - atom
  - coding
Topics:
  - DSA
  - Stack
---
``` c++
class Solution {
  public:
    int celebrity(vector<vector<int>>& mat) {
        int n = mat.size();
        stack<int> s;
        for(int i = 0; i< n; i++){
            s.push(i);
        }
        while(s.size() > 1){
            int a = s.top();
            s.pop();
            int b = s.top();
            s.pop();
            
            // a knows b
            if(mat[a][b] == 1){
                s.push(b);
            }
            else{
                s.push(a);
            }
        }
        int c = s.top();
        int flag = 0;
        // celebrity knows no-one
        for(int i = 0; i < n; i++){
            if(c != i){
                if(mat[c][i] == 1){
                    flag = 1;
                    break;
                }
            }
        }
        
        if(flag == 1) return -1;
        
        //check everybody knows celebrity
        for(int j = 0; j < n; j++){
            if(j != c){
                if(mat[j][c] == 0){
                    flag = 1;
                    break;
                }
            }
        }
        
        if(flag == 1) return -1;
        return c;
        
    }
};
```
