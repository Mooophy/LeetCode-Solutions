### 64. Minimum Path Sum
* `Dynamic Programming`
* O(m * n), O(m * n)
* C++(Top Down)
```cpp
class Solution {
    
    int encode(int r, int c){
        return r << 15 | c;
    }
    
public:
    int minPathSum(vector<vector<int>>& g) {
        unordered_map<int, int> memo;
        return g.empty() ? 0 : dp(0, 0, g, memo);
    }
    
    int dp(int r, int c, vector<vector<int>> const& g, unordered_map<int, int>& memo){
        int m = g.size(), n = g[0].size();
        auto code = encode(r, c);
        
        if(memo.count(code)){
            return memo.at(code);
        }
        
        if(r == m - 1 && c == n - 1){
            return memo[code] = g[r][c]; 
        } 
        
        int res = numeric_limits<int>::max();
        
        if(r + 1 < m){
            res = min(res, g[r][c] + dp(r + 1, c, g, memo));
        }
        
        if(c + 1 < n){
            res = min(res, g[r][c] + dp(r, c + 1, g, memo));
        }
        
        return memo[code] = res;
    }
};
```
