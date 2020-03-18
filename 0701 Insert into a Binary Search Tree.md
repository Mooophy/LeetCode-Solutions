### 701. Insert into a Binary Search Tree
* `BST`
* C++
```cpp
class Solution {
public:
    TreeNode* insertIntoBST(TreeNode* root, int val) {
        insert(root, val);
        return root;
    }
    
    void insert(TreeNode *& root, int val){
        if(!root){
            root = new TreeNode(val);
            return;
        }
        
        insert(root->val > val ? root->left : root->right, val);
    }
};
```
