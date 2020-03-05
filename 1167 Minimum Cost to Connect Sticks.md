### 1167. Minimum Cost to Connect Sticks
* `Greedy`
* O(n * lg(n)), O(n)
* Loop Invariant: 
```
Sticks are connected and cost recorded while the min heap is shrinking towards size = 1
```
* Proof
```
Suppose set A holds all sticks, then for any iteration there exists equations such that:

x := argmin(A)
y := argmin(A - {x})
f(A) => x + y + f(A - {x} - {y} + {x + y})

As shown above, the local optimal option can lead to global optimal option. 
Hence, Greedy applies, DP is unnecessary.
```
* C++
```cpp
class Solution {
    using MinHeap = priority_queue<int, vector<int>, greater<int>>;
    
public:
    int connectSticks(vector<int>& sticks) {
        MinHeap q(sticks.begin(), sticks.end());
        int cost = 0;
        
        for(int x = 0, y = 0; q.size() > 1; cost += x + y){
            x = q.top(); q.pop();
            y = q.top(); q.pop();
            q.push(x + y);
        }
        
        return cost;
    }
};
```
