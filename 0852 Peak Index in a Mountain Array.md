### 852. Peak Index in a Mountain Array
* `Binary Search`
* O(lg(n)), O(1)
* Compare `A[mid]` with `A[mid - 1]` and `A[mid + 1]` respectively, go left or right depending on the comparison result.
* C++
```cpp
class Solution {
public:
    int peakIndexInMountainArray(vector<int>& A) {
        int n = A.size();
        
        for(int l = 0, r = n - 1; l <= r; ){
            int mid = (l + r) / 2;
            
            if(A[mid] < A[mid - 1]){
                r = mid - 1;
                continue;
            }
            
            if(A[mid] < A[mid + 1]){
                l = mid + 1;
                continue;
            }
            
            return mid;
        }
        
        return -1;
    }
};
```
* C#
```csharp
public class Solution {
    public int PeakIndexInMountainArray(int[] A) {
        int n = A.Length;
        
        for(int l = 0, r = n - 1; l <= r; ){
            int mid = (l + r) / 2;
            
            if(A[mid] < A[mid - 1]){
                r = mid - 1;
                continue;
            }
            
            if(A[mid] < A[mid + 1]){
                l = mid + 1;
                continue;
            }
            
            return mid;
        }
        
        return -1;        
    }
}
```
