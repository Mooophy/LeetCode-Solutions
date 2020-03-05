### 67. Add Binary
* O(n), O(1)
* Loop Invariant: The sum have been written into res if any condition is true: i has not reached end, j has not reached end, carry exists.
* C++
```cpp
class Solution {
public:
    string addBinary(string a, string b) {
        string res;
        
        for(int i = a.size() - 1, j = b.size() - 1, carry = 0; i >= 0 || j >= 0 || carry; i -= i >= 0, j -= j >= 0){
            int froma = i >= 0 ? (a.at(i) - '0') : 0;
            int fromb = j >= 0 ? (b.at(j) - '0') : 0;
            int sum   = froma + fromb + carry;
            carry     = sum / 2;
            res.insert(0, 1, sum % 2 + '0');
        }
        
        return res;
    }
};
```
