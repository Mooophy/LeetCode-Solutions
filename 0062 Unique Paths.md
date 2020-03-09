### 62. Unique Paths
* `Dynamic Programming`
* O(m * n), O(m * n)
* C++ (Top Down)
```cpp
class Solution {
    
    int encode(int r, int c){
        return r << 10 | c;
    }
    
public:
    int uniquePaths(int m, int n) {
        unordered_map<int, int> memo;
        
        return dp(0, 0, m, n, memo);            
    }
    
    int dp(int r, int c, int m, int n, unordered_map<int, int>& memo){
        int code = encode(r, c);
        
        if(memo.count(code)){
            return memo.at(code);
        }
        
        if(r == m - 1 && c == n - 1){
            return memo[code] = 1;
        }
        
        int rht = r + 1 < m ? dp(r + 1, c, m, n, memo) : 0;
        int dwn = c + 1 < n ? dp(r, c + 1, m, n, memo) : 0;
        
        return memo[code] = rht + dwn;
    }
};
```
