**Diameter of binary tree**
```
class Solution {
public:
    int ans=0;
    int diam(TreeNode* root){
        if(root==NULL)return 0;
        int lh=diam(root->left);
        int rh= diam(root->right);
        ans= max(lh+rh,ans);
        return max(lh,rh)+1;
    }
    int diameterOfBinaryTree(TreeNode* root) {
        diam(root);
        return ans;
    }
};
```
<img width="1919" height="906" alt="image" src="https://github.com/user-attachments/assets/e6321c0e-9f62-4d24-8c2b-0215cdfe8cc6" />  

**Lowest common ancestor of a binary tree**
```
class Solution {
public:
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        if(root==NULL){
            return NULL;
        }
        if(p==root || q==root){
            return root;
        }
        TreeNode* lc= lowestCommonAncestor(root->left,p,q);
        TreeNode* rc= lowestCommonAncestor(root->right,p,q);
        if(lc && rc){
            return root;
        }else if(lc!=NULL){
            return lc;
        }else{
            return rc;
        }
    }
};
```
<img width="1919" height="910" alt="image" src="https://github.com/user-attachments/assets/f11b587e-b3cc-4e6b-990f-f11c836165bd" />  

**Recover binary search tree**
```
class Solution {
public:
    TreeNode* first=NULL;
    TreeNode* second=NULL;
    TreeNode* prev=NULL;
    void inorder(TreeNode* root){
        if(!root)return;
        inorder(root->left);
        if(prev && prev->val>root->val){
            if(!first)first=prev;
            second=root;
        }
        prev=root;
        inorder(root->right);
    }
    void recoverTree(TreeNode* root) {
        if(root==NULL)return;
        inorder(root);
        swap(first->val,second->val);
    }
};
```
<img width="1913" height="928" alt="image" src="https://github.com/user-attachments/assets/eef6b5ce-a1d4-4314-b0fe-37e37fc0f25a" />
