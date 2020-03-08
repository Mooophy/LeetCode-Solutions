### 678. Valid Parenthesis String
* `Dynamic Programming`
* O(n ^ 2), O(n ^ 2)
* C++(DP with Top down)
```cpp
class Solution {
    
    int encode(int i, int open){
        return i << 12 | open;
    }
    
public:
    bool checkValidString(string s) {
        unordered_map<int, bool> memo;
        
        return dp(0, 0, s, memo);
    }
    
    bool dp(int i, int open, string const& s, unordered_map<int, bool>& memo){
        auto code = encode(i, open);
        
        if(memo.count(code)){
            return memo.at(code);
        }
        
        if(i == s.size()){
            return memo[code] = 0 == open;
        }
        
        auto o = dp(i + 1, open + 1, s, memo);
        auto c = open > 0 && dp(i + 1, open - 1, s, memo);
        
        if(s.at(i) == '('){
            return memo[code] = o;
        }
        
        if(s.at(i) == ')'){
            return memo[code] = c;
        }
        
        return memo[code] = o || c || dp(i + 1, open, s, memo);
    }
};
```
