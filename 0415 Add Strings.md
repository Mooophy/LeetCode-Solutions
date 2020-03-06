### 415. Add Strings

* O(n), O(1)
* C++
```cpp
class Solution {
public:
    string addStrings(string a, string b) {
        string res;
        
        for(int i = a.size() - 1, j = b.size() -1, carry = 0; i >= 0 || j >= 0 || carry; i -= i >= 0, j -= j >= 0){
            int bya = i >= 0 ? (a.at(i) - '0') : 0;
            int byb = j >= 0 ? (b.at(j) - '0') : 0;
            int sum = bya + byb + carry;
            carry = sum / 10;
            res.push_back(sum % 10 + '0');
        }
        
        reverse(res.begin(), res.end());
        
        return res;
    }
};
```
