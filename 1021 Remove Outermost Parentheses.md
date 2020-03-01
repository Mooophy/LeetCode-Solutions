### 1021. Remove Outermost Parentheses.md
* `Stack`
* O(n), O(1)
* Although tagged with `Stack`, a counter is enough.
* C++
```cpp
class Solution {
public:
    string removeOuterParentheses(string s) {
        int count = 0;
        string res;
        
        for(auto c : s){
            if(c == '('){
                if(++count > 1){
                    res += c;
                }
            }else{
                if(--count > 0){
                    res += c;
                }
            }
        }
        
        return res;
    }
};
```
* C#
```csharp
public class Solution {
    public string RemoveOuterParentheses(string s) {
        string res = "";
        int count = 0;
        
        foreach(var c in s){
            if(c == '('){
                if(++count > 1){
                    res += c;
                }
            }else{
                if(--count > 0){
                    res += c;
                }
            }
        }
        
        return res;
    }
}
```
