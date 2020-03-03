### 746. Min Cost Climbing Stairs

* `Dynamic Programming`
* O(n), O(n) / O(n), O(1)
* Draw a DAG to show the process.
* C++ (Top Down)
```cpp
class Solution {
public:
    
    //
    // O(n), O(n)
    //
    
    int minCostClimbingStairs(vector<int>& cost) {
        unordered_map<int, int> memo;
        return min(f(0, cost, memo), f(1, cost, memo));
    }
    
    int f(int n, vector<int> const& cost, unordered_map<int, int>& memo){
        if(memo.count(n)){
            return memo.at(n);
        }
        
        if(n >= cost.size()){
            return memo[n] = 0;
        }
        
        int option1 = cost.at(n) + f(n + 1, cost, memo);
        int option2 = cost.at(n) + f(n + 2, cost, memo);
        
        return memo[n] = min(option1, option2);
    }
};
```

* C++ (Bottom Up)
```cpp
class Solution {
public:

    //
    // O(n), O(1)
    //
    
    int minCostClimbingStairs(vector<int>& cost) {
        int dp1 = 0, dp2 = 0;
        
        for(int i = 2; i <= cost.size(); ++i){
            auto option1 = dp1 + cost.at(i - 1);
            auto option2 = dp2 + cost.at(i - 2);
            dp2 = dp1;
            dp1 = min(option1, option2);
        }
        
        return dp1;
    }
};

```
* Dag
![GitHub Logo](/pics/dag0746.png)

* C#(Skipped)
