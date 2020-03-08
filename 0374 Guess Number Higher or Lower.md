### 374. Guess Number Higher or Lower
* `Binary Search`
* O(lg(n)), O(1)
* C++
```cpp
int guess(int num);

class Solution {
public:
    int guessNumber(int n) {
        for(int l = 1, r = n; l <= r; ){
            int m = l / 2 + r / 2 + ((l & 1) && (r & 1) ? 1 : 0);
            int ans = guess((int)m); 
            
            if(!ans){
                return m;
            }
            
            if(ans > 0){
                l = m + 1;
            }else{
                r = m - 1;
            }
        }
        
        return -1;
    }
};
```
