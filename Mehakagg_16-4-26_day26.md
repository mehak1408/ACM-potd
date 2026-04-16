**Invert binary tree**
```
class Solution {
public:
    TreeNode* invertTree(TreeNode* root) {
        if(root==NULL){
            return NULL;
        }
        TreeNode* temp=root->left;
        root->left=root->right;
        root->right=temp;
        invertTree(root->left);
        invertTree(root->right);
        return root;
    }
};
```
<img width="1919" height="864" alt="image" src="https://github.com/user-attachments/assets/21e47360-6c9d-4a39-b0d8-324066ca4da5" />  

**Kth smallest element in BST**
```
class Solution {
public:
    int cnt=0,ans=-1;
    void inorder(TreeNode* root,int k){
        if(!root)return;
        inorder(root->left,k);
        cnt++;
        if(cnt==k){ans=root->val; return;}
        inorder(root->right,k);
    }
    int kthSmallest(TreeNode* root, int k) {
        inorder(root,k);
        return ans;
    }
};
```
<img width="1919" height="903" alt="image" src="https://github.com/user-attachments/assets/9017ef8e-cc72-43ea-927c-3626bc3cbbd0" />
