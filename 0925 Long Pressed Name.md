### 925. Long Pressed Name
* `Two Pointers`
* O(n), O(1)
* Loop Invariant: `j has not reached end and only normal copy and long pressed has been encountered so far.`
* Detail: There two cases here, copy and long (pressed), both normal. If both failed then return false. After j has reached end, i must reach its end as well. Otherwise, there are letters left in string `name`. This case also yields false.
* C++
```cpp
class Solution {
public:
    bool isLongPressedName(string name, string type) {
        int i = 0, m = name.size(), n = type.size();
        
        for(int j = 0; j < n; ++j){
            bool is_copy = i < m && name.at(i) == type.at(j);
            bool is_long = j > 0 && type.at(j) == type.at(j - 1); 
            
            if(!is_copy && !is_long){
                return false;
            }
            
            i += is_copy;
        }
        
        return i == m;
    }
};
```
