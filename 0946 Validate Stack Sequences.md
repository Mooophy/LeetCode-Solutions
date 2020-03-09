### 946. Validate Stack Sequences
* `Stack`, `Two Pointers`
* O(n), O(n)
* LI: 
```
popped[0...j) have been checked.
```
* Note: Since pop happens after pushing, so once popped have been validated then all done.
* C++
```cpp
class Solution {
public:
    bool validateStackSequences(vector<int>& pushed, vector<int>& popped) {
        vector<int> stk;
        
        for(int i = 0, j = 0; j < popped.size(); ){
            if(stk.size() && stk.back() == popped.at(j)){
                stk.pop_back();
                ++j;
            }else if(i < pushed.size()){
                stk.push_back(pushed.at(i++));
            }else{
                return false;    
            }
        }        
        
        return true;
    }
};
```
