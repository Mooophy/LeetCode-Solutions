### 653. Two Sum IV - Input is a BST
* `Tree`, `Dfs`
* O(n * lg(n)), O(1)
* Idea: Traverse the tree with dfs, then search `k - root->val` in the BST. Quite a few other solutions exisit.
* C++
```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
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
