### 925. Long Pressed Name
* `Two Pointers`
* O(n), O(1)
* li
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
