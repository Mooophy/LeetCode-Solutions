### 70. Climbing Stairs
* `Dynamic Programming`
* O(n), O(1)
* f(n) = f(n - 1) + f(n - 2)
* C++
```cpp
class Solution {
public:

    //
    // DP : Bottom Up
    //

    int climbStairs(int n) {
        if(n <= 2){
            return n;
        }
        
        int dp2 = 1, dp1 = 2;
        
        for(int i = 3; i <= n; ++i){
            auto curr = dp2 + dp1;
            dp2 = dp1;
            dp1 = curr;
        }
        
        return dp1;
    }
};
```
* C#(Skipped)
* Dag
![GitHub Logo](/pics/dag0746.png)
