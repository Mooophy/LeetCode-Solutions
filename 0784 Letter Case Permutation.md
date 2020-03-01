### 0784. Letter Case Permutation

* `Backtracking`
* O(2 ^ n), O(2 ^ n)
* Each node spawns 1 child for digit char, 2 children for alphabet char.
* C++
```cpp
class Solution {
public:
    vector<string> letterCasePermutation(string s) {
        vector<string> res;
        dfs("", s, res);
        return res;
    }
    
    void dfs(string curr, string const& s, vector<string>& res){
        if(curr.size() == s.size()){
            res.push_back(curr);
            return;
        }
        
        auto i = curr.size();
        
        if(isdigit(s.at(i))){
            dfs(curr + string(1, s.at(i)), s, res);
            return;
        }
        
        dfs(curr + string(1, tolower(s.at(i))), s, res);
        dfs(curr + string(1, toupper(s.at(i))), s, res);
    }
};
```
* C#
```csharp
public class Solution {
    public IList<string> LetterCasePermutation(string s) {
        var res = new List<string>();
        Dfs("", s, res);
        return res;
    }
    
    private void Dfs(string curr, string s, IList<string> res){
        if(curr.Length == s.Length){
            res.Add(curr);
            return;
        }        
        
        var i = curr.Length;

        if(Char.IsDigit(s[i])){
            Dfs(curr + s[i], s, res);
            return;
        }

        Dfs(curr + Char.ToLower(s[i]), s, res);
        Dfs(curr + Char.ToUpper(s[i]), s, res);           
    }
}
```
