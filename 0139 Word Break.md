### 139. Word Break

* `Dynamic Programming`
* O(s.size * dic.size), O(s.size * dic.size)
* C++ (Top Down)
```cpp
class Solution {
public:
    bool wordBreak(string s, vector<string>& dic) {
        vector<int> memo(s.size() + 1, -1);
        return dp(0, s, dic, memo);
    }
    
    bool dp(int i, string const& s, vector<string>& dic, vector<int>& memo){
        if(memo.at(i) >= 0){
            return memo.at(i);
        }
        
        if(i == s.size()){
            return memo[i] = true;
        }
        
        bool res = false;
        
        for(auto const& word : dic){
            if(s.find(word, i) == i){
                res |= dp(i + word.size(), s, dic, memo);
            }
        }
        
        return memo[i] = res;
    }
};
```
