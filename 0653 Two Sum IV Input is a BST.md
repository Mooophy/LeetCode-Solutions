### 653. Two Sum IV - Input is a BST
* `Tree`, `Dfs`
* O(n * lg(n)), O(1)
* Idea: Traverse the tree with dfs, then search `k - root->val` in the BST. Quite a few other solutions exisit.
* C++
```cpp
class Solution {
    
public:
    
    //
    // O(n * lg(n)), O(1)
    //
    
    bool findTarget(TreeNode* root, int k) {
        return dfs(root, root, k);
    }
    
    bool dfs(TreeNode* curr, TreeNode* root, int k){
        if(!curr){
            return false;
        }
        
        if(2 * curr->val != k && search(root, k - curr->val)){
            return true;
        }
        
        return dfs(curr->left, root, k) || dfs(curr->right, root, k);
    }
    
    bool search(TreeNode* root, int val){
        if(!root){
            return false;
        }
        
        if(root->val == val){
            return true;
        }
        
        if(val > root->val){
            return search(root->right, val);
        }
        
        return search(root->left, val);
    }
};
```

* C#
```csharp
public class Solution {
    public bool FindTarget(TreeNode root, int k) {
        return Dfs(root, root, k);
    }
    
    private bool Dfs(TreeNode curr, TreeNode root, int k){
        if(curr == null){
            return false;
        }
        
        if(2 * curr.val != k && Search(root, k - curr.val)){
            return true;
        }
        
        return Dfs(curr.left, root, k) || Dfs(curr.right, root, k);
    }
    
    private bool Search(TreeNode root, int val){
        if(root == null){
            return false;
        }
        
        if(root.val == val){
            return true;
        }
        
        if(val > root.val){
            return Search(root.right, val);
        }
        
        return Search(root.left, val);
    }    
}
```
