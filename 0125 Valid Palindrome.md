### 125. Valid Palindrome
* `Two Pointers`
* O(n) O(1)
* Loop invariant: `The two parts [0...i) and (j...end - 1] where i < j have been validated and not failed yet`
* C++
```cpp
class Solution {
public:
    bool isPalindrome(string s) {
        for(int n = s.size(), i = 0, j = n - 1; ; ++i, --j){
            for(; i < j && !isalnum(s.at(i)); ++i);
            for(; i < j && !isalnum(s.at(j)); --j);

            if(i >= j){
                return true;
            }
            
            if(tolower(s.at(i)) != tolower(s.at(j))){
                return false;
            }
        }
        
        return true;
    }
};
```
