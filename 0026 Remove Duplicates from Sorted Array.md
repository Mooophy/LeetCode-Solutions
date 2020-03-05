### 26. Remove Duplicates from Sorted Array
* `Two Pointers`
* O(n), O(1)
* Loop Invariant: `Elements from a[0...i) have been written to a[0...end) with duplicated removed`
* C++
```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& a) {
        if(a.empty()){
            return 0;
        }
        
        int end = 1;
        
        for(int i = 1, n = a.size(); i < n ; ++i){
            if(a.at(i) != a.at(i - 1)){
                a[end++] = a.at(i);
            }
        }
        
        return end;
    }
};
```
