### 680. Valid Palindrome II

* `Two Pointers`
* O(n), O(1)
*
* C++
```cpp
class Solution {
public:
    bool validPalindrome(string s) {
        int i = 0, j = s.size() - 1;
        for( ; i < j && s.at(i) == s.at(j); ++i, --j);
        
        if(i >= j){
            return true;
        }
        
        int a = i + 1, b = j;
        for( ; a < b && s.at(a) == s.at(b); ++a, --b);
        
        if(a >= b){
            return true;
        }
        
        int x = i, y = j - 1;
        for( ; x < y && s.at(x) == s.at(y); ++x, --y);
        
        return x >= y;
    }
};
```
