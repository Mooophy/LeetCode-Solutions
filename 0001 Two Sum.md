### 1. Two Sum
* O(n), O(n)
* Loop Invariant: `There is no element from [ a[0] ... a[i] ) that is equale to target - a[i]`
* C++
```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> hash;
        
        for(int i = 0; i < nums.size(); ++i){
            if(hash.count(target - nums.at(i))){
                return { hash[target - nums.at(i)], i };
            }
            
            hash[nums.at(i)] = i;
        }
        
        return { -1, -1 };
    }
};
```
* C#
```csharp
public class Solution {
    public int[] TwoSum(int[] nums, int target) {
        var hash = new Dictionary<int, int>();
        
        for(int i = 0; i < nums.Length; ++i){
            if(hash.ContainsKey(target - nums[i])){
                return new int[]{ hash[target - nums[i]], i };
            }
            
            if(!hash.ContainsKey(nums[i])){
                hash.Add(nums[i], i);    
            }
        }
        
        return new int[]{ -1, -1 };
    }
}
```
