### 414. Third Maximum Number
* std::set is more proper than std::priority_queue, because set removes duplicates
* C++
```cpp
class Solution {
public:
    int thirdMax(vector<int>& nums) {
        set<int> q;

        for(auto n : nums){
            q.insert(n);
            
            if(q.size() > 3){
                q.erase(q.begin());
            }
        }
        
        return q.size() == 3 ? *q.begin() : *q.rbegin();
    }
};
```
