### 150. Evaluate Reverse Polish Notation
* `Stack`
* O(n), O(n)
* C++
```cpp
class Solution {
public:
    int evalRPN(vector<string>& tokens) {
        vector<string> stk;
        
        for(auto const& t : tokens){
            if(isdigit(t.back())){
                stk.push_back(t);
            }else{
                int y = stoi(stk.back()); stk.pop_back();
                int x = stoi(stk.back()); stk.pop_back();
                
                if(t == "+"){
                    stk.push_back(to_string(x + y));
                }
                if(t == "-"){
                    stk.push_back(to_string(x - y));
                }
                if(t == "*"){
                    stk.push_back(to_string(x * y));
                }
                if(t == "/"){
                    stk.push_back(to_string(x / y));
                }
            }
        }
        
        return stoi(stk.back());
    }
};
```
