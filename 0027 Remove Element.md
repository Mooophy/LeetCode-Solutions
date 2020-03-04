### 27. Remove Element
* `Two Pointers`
* O(n), O(1)
* Loop invariant : `a[0..tail - 1] stores elements without target elments, with tail pointing to the new size`
* C++
```cpp
class Solution {
public:
    int removeElement(vector<int>& a, int t) {
        int tail = 0;
        
        for(int i = 0; i < a.size(); ++i){
            if(a.at(i) != t){
                a[tail++] = a.at(i);
            }
        }
        
        return tail;
    }
};
```
