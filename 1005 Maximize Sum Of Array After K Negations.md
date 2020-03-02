### 1005. Maximize Sum Of Array After K Negations
* Greedy
* O(n lg(n)), O(1)
* C++
```cpp
class Solution {
public:
    int largestSumAfterKNegations(vector<int>& a, int k) {
        sort(a.begin(), a.end());
        
        for(auto& n : a){
            if(k == 0 || n >= 0){
                break;
            }
            n = -n;
            --k;
        }
        
        return accumulate(a.begin(), a.end(), 0) - 2 * (k & 1) * *min_element(a.begin(), a.end());
    }
};
```
