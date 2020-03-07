### 49. Group Anagrams

* `Hash Table`
* O(n * len * lg(len)), O(n) where len is the length of each string
* C++
```cpp
class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        unordered_map<string, vector<int>> hash;
        
        for(int i = 0; i < strs.size(); ++i){
            auto key(strs.at(i));
            sort(key.begin(), key.end());
            hash[key].push_back(i);
        }
        
        vector<vector<string>> res;
        
        for(auto const& pair : hash){
            res.push_back({});
            
            for(auto i : pair.second){
                res.back().push_back(strs.at(i));
            }
        }
        
        return res;
    }
};
```
