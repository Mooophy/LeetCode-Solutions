### 724. Find Pivot Index
* O(n), O(1)
* LI: 
```r
For range [0, i), sum of a[0 .. i - 1] is not equal to sum of a[i + 1 .. end)
```
* C++
```cpp
class Solution {
public:
    int pivotIndex(vector<int>& a) {
        for(int l = 0, r = accumulate(a.begin(), a.end(), 0), i = 0; i < a.size(); ++i){
            if(l == r - a.at(i)){
                return i;
            }
            
            l += a.at(i);
            r -= a.at(i);
        }        
        
        return -1;
    }
};
```
