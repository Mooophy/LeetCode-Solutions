### 7. Reverse Integer
* `Math`
* O(sizeof(int)), O(1)
* Notes: 1. res must be 64bits to avoid overflow. 2. `-` can be processed with `/` and `%` correctly. 3.Except type casting is more strict for C#, the rest is same thing for the two languages.
* C++
```cpp
class Solution {
public:
    int reverse(int x) {
        int64_t res = 0;
        
        for(; x; x /= 10){
            res = 10 * res + x % 10;
        }
        
        return res > numeric_limits<int>::max() ||  res < numeric_limits<int>::min() ? 0 : res;
    }
};
```

* C#
```csharp
public class Solution {
    public int Reverse(int x) {
        long res = 0;
        
        for(; x != 0; x /= 10){
            res = 10 * res + x % 10;
        }
        
        return Convert.ToInt32(res > Convert.ToInt64(Int32.MaxValue) ||  res < Convert.ToInt64(Int32.MinValue) ? 0 : res);        
    }
}
```
