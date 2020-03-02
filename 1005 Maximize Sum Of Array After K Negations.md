### 1005. Maximize Sum Of Array After K Negations
* Greedy
* O(n lg(n)), O(1)
* There exists O(n) solution with Counting Sort.
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
* C#
```csharp
public class Solution {
    public int LargestSumAfterKNegations(int[] A, int K) {
        Array.Sort(A);
        
        for(int i = 0; i < A.Length && K > 0 && A[i] < 0; ++i, --K){
            A[i] = - A[i];
        }
        
        return A.Sum() - 2 * (K & 1) * A.Min();
    }
}
```
