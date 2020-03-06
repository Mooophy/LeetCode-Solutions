### 830. Positions of Large Groups
* O(n), O(1)
* LI: 
```
All large groups amoung s[0, i) have been recorded in res
```
* C++
```cpp
class Solution {
public:
    vector<vector<int>> largeGroupPositions(string s) {
        vector<vector<int>> res;
        
        for(int i = 0, n = s.size(); i < n; ){
            int j = i + 1;
            for(; j < n && s.at(j) == s.at(i); ++j);
            
            if(j - i >= 3){
                res.push_back({i, j - 1});
            }
            
            i = j;
        }
        
        return res;
    }
};
```
