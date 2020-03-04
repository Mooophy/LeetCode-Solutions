### 198. House Robber

* `Dynamic Programming`
* O(n), O(1)
* f(n) = max(a[n] + f(n - 2), f(n - 1))
* Dag:
![GitHub Logo](/pics/dag0746.png)
* C++
```cpp
class Solution {
public:
    
    //
    // Bottom Up
    //
    
    int rob(vector<int> const& a) {
        int n = a.size() - 1;
        int dp2 = 0;
        
        if(n < 0){
            return dp2;
        }
        
        int dp1 = a.at(0);
        
        if(n == 0){
            return dp1; 
        }
        
        for(int i = 1; i <= n; ++i){
            int cur = max(dp1, a.at(i) + dp2);
            dp2 = dp1;
            dp1 = cur;
        }
        
        return dp1;
    }
};
```
* C#(Skipped)
