### 1087. Brace Expansion
* `Backtracking`, `Dfs`
* O(a ^ n) where a <- (0, s.size()), O(1) (ignore space overhead for result and recursion)
* Loop Invariant: `Spawn children by appending opions at i into child passed in`
* C++
```cpp
class Solution {
public:
    vector<string> expand(string s) {
        vector<string> res;
        fill("", 0, res, s);
        sort(res.begin(), res.end());
        return res;
    }
    
    void fill(string curr, int i, vector<string>& res, string const& s){
        if(i == s.size()){
            res.push_back(curr);
            return;
        }
        
        if(isalpha(s.at(i))){
            fill(curr + s.at(i), i + 1, res, s);
            return;
        }
        
        vector<char> options;
        
        for(; s.at(i) != '}'; ++i){
            if(isalpha(s.at(i)))
                options.push_back(s.at(i));
        }
        
        for(auto c : options){
            fill(curr + c, i + 1, res, s);
        }
    }
};
```
