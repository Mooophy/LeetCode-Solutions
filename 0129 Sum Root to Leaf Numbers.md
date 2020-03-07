### 129. Sum Root to Leaf Numbers
* `DFS`
* O(n), O(1)
* C++
```cpp
class Solution {
public:
    int sumNumbers(TreeNode* root) {
        int res = 0;
        dfs(root, res, 0);
        return res;
    }
    
    void dfs(TreeNode* root, int& res, int n){
        if(!root){
            return;
        }
        
        n = n * 10 + root->val;
        bool is_leaf = !root->left && !root->right; 
        res += is_leaf ? n : 0;  
        
        dfs(root->left , res, n);
        dfs(root->right, res, n);
    }
};
```
