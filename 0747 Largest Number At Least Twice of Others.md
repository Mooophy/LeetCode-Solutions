### 747. Largest Number At Least Twice of Others
* Array
* O(n) O(1)
* Loop Invariant: `The maximum and second to maximum values have been found within A[0, i)`
* C++
```cpp
class Solution {
public:
    int dominantIndex(vector<int>& a) {
        int fst = 0, idx = 0, snd = 0;
        
        for(int i = 0; i < a.size(); ++i){
            if(a.at(i) > fst){
                snd = fst;
                fst = a.at(i);
                idx = i;
            }else if(a.at(i) > snd){
                snd = a.at(i);
            }
        }
        
        return fst >= 2 * snd ? idx : -1;
    }
};
```
