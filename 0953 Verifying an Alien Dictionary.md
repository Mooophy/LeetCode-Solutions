### 953. Verifying an Alien Dictionary
* `Hash Table`
* O(n * s), O(1)
* Build the hash table for the language. Then check if it is sorted with a lamabda
* A lexicographical comparison is the kind of comparison generally used to sort words alphabetically in dictionaries; It involves comparing sequentially the elements that have the same position in both ranges against each other until one element is not equivalent to the other. The result of comparing these first non-matching elements is the result of the lexicographical comparison.

If both sequences compare equal until one of them ends, the shorter sequence is lexicographically less than the longer one.
* C++
```cpp
class Solution {
    
public:
    
    //
    // O(words.size() * s.size()), O(1)
    //
    
    bool isAlienSorted(vector<string>& words, string order) {
        auto language = toLanguage(order);
        
        auto less = [&](string const& l, string const& r){
            int i = 0;
            
            for(; i < l.size() && i < r.size(); ++i){
                if(language.at(l.at(i) - 'a') == language.at(r.at(i) - 'a')){
                    continue;
                }else{
                    return language.at(l.at(i) - 'a') < language.at(r.at(i) - 'a');
                }    
            }
            
            return l.size() < r.size(); 
        };
   
        return is_sorted(words.begin(), words.end(), less);
    }
    
    vector<int> toLanguage(string const& s){
        vector<int> res(26, 0);
        int count = 0;
        
        for(auto c : s){
            res[c - 'a'] = count++;
        }
        
        return res;
    }
};
```
