### 139. Word Break

* `Dynamic Programming`
* O(s.size * dic.size), O(s.size * dic.size)
* Analysis: The fact that word size is always > 0 implies that there is no cycle involved. In another word it's a DAG and thus can be solved by DP. With that being said, this DAG is hard to draw before running time, because the edges are determined by the input.
* Loop Invariant:
```
s[0, i) has been confirmed that it can be segmented into one or more dictionary words.
```
* C++ (Top Down)
```cpp
class Solution {
public:
    bool wordBreak(string s, vector<string> const& dic) {
        vector<int> memo(s.size() + 1, -1);
        return dp(0, s, dic, memo);
    }
    
    bool dp(int i, string const& s, vector<string> const& dic, vector<int>& memo){
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
