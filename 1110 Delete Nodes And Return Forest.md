### 1110. Delete Nodes And Return Forest
* `DFS`, `Post Order Traversal`
* C++
```cpp
class Solution {
public:
    vector<TreeNode*> delNodes(TreeNode* root, vector<int>& to_delete) {
        unordered_set<int> hash(to_delete.begin(), to_delete.end());
        vector<TreeNode*> res;
        postorder(root, hash, res);
        
        if(root && !hash.count(root->val)){
            res.push_back(root);
        }
        
        return res;
    }
    
    void postorder(TreeNode *& root, unordered_set<int> const& hash, vector<TreeNode*>& res){
        if(!root){
            return;
        }
        
        postorder(root->left , hash, res);
        postorder(root->right, hash, res);
        
        if(hash.count(root->val)){
            if(root->left){
                res.push_back(root->left);
            }
            
            if(root->right){
                res.push_back(root->right);
            }
            
            root = nullptr;
        }
    }
};
```
