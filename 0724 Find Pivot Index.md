### 724. Find Pivot Index
* O(n), O(1)
* LI: `ss`
* C++
```cpp
class Solution {
public:
    int pivotIndex(vector<int>& a) {
        int res = -1;
        
        for(int l = 0, r = accumulate(a.begin(), a.end(), 0), i = 0; i < a.size(); ++i){
            if(l == r - a.at(i)){
                return i;
            }
            
            l += a.at(i);
            r -= a.at(i);
        }        
        
        return res;
    }
};
```
