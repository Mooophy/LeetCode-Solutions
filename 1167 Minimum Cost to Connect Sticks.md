### 1167. Minimum Cost to Connect Sticks
* `Greedy`
* O(n * lg(n)) O(n)
* Loop Invariant: `Sticks are connected and cost recorded while the size of the min heap is shrinking towards 1`
* Proof
```
Suppose set A holds all sticks
x := argmin(A)
y := argmin(A - {x})
f(A) => x + y + f(A - {x} - {y} + {x + y}) 
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
