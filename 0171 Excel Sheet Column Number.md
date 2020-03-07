### 171. Excel Sheet Column Number
* O(n), O(1)
* Note how to deal with the offset, since A is 1, rather than 0
* C++
```cpp
class Solution {
public:
    int titleToNumber(string s) {
        int res = 0;
        
        for(auto c : s){
            res = res * 26 + (c - 'A' + 1); 
        }
        
        return res;
    }
};
```
