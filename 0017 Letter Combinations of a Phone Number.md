### 17. Letter Combinations of a Phone Number
* `Backtracking`
* O(4 ^ n), O(1)
* C++
```cpp
class Solution {
    
    vector<string> map = { "abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv","wxyz" };
    
public:
    vector<string> letterCombinations(string digits) {
        if(digits.empty()){
            return {};
        }
        
        vector<string> res;
        dfs(0, "", digits, res);
        
        return res;
    }
    
    void dfs(int i, string curr, string const& digits, vector<string>& res){
        if(i == digits.size()){
            res.push_back(curr);
            return;
        }
        
        for(auto c : map.at(digits.at(i) - '2')){
            dfs(i + 1, curr + c, digits, res);
        }
    }
};
```
