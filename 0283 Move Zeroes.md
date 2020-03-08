### 283. Move Zeroes
* `Two Pointers`
* O(n), O(1)
* C++
```cpp
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        int i = 0, n = nums.size();
        
        for(auto& n : nums){
            if(n){
                nums[i++] = n;
            }
        }
        
        for(; i < n; nums[i++] = 0);
    }
};
```
