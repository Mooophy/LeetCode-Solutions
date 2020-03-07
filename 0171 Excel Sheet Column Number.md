### 171. Excel Sheet Column Number
* O(n), O(1)
* Note how to deal with the offset, since A is 1, rather than 0
* C++
```cpp
class Solution {
public:
    int titleToNumber(string s) {
        int res = 0;
        
        for(int64_t at = 1, i = s.size() - 1; i >= 0; --i, at *= 26){
            res += at * (s.at(i) - 'A' + 1); 
        }
        
        return res;
    }
};
```
