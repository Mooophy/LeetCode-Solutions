### 1221. Split a String in Balanced Strings
* `Greedy`
* O(n), O(1)
* Proof:
g(s0) = 1 + g(s1) where s1 is the string trimmed with the first balanced string. This proof looks quite similar to Theorem 16.1 on CLRS

* C++
```cpp
    int balancedStringSplit(string s) {
        int balance = 0, res = 0;
        
        for(auto c : s){
            balance += c == 'R' ? 1 : -1;
            res += balance == 0;
        }
        
        return res;
    }
```
* C#
```csharp
    public int BalancedStringSplit(string s) {
        int balance = 0, res = 0;
        
        foreach(var c in s){
            balance += c == 'R' ? 1 : -1;
            res += balance == 0 ? 1 : 0;
        }
        
        return res;
    }
```
