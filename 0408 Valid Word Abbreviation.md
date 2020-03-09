### 408. Valid Word Abbreviation
* `Two Pointers`
* O(n), O(1)
* C++
```cpp
class Solution {
public:
    bool validWordAbbreviation(string word, string abbr) {
        int m = word.size(), n = abbr.size(), i = 0, j = 0;
        
        while(i < m && j < n){
            if(isalpha(abbr.at(j))){
                if(abbr.at(j) != word.at(i)){
                    return false;
                }
                ++i;
                ++j;
            }else if(abbr.at(j) == '0'){ // check for leading zeroes
                return false;
            }else{
                int k = j + 1;
                for(; k < n && isdigit(abbr.at(k)); ++k);
                i += stoi(abbr.substr(j, k - j));
                j = k;
            }
        }
        
        return i == m && j == n;
    }
};
```
