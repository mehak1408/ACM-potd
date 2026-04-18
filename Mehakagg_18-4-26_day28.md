**subtree of another tree**
```
class Solution {
public:
    bool isid(TreeNode* root, TreeNode* subroot){
        if(!root && !subroot)return true;
        if(!root || !subroot)return false;
        if(root->val!=subroot->val)return false;
        return isid(root->left,subroot->left) && isid(root->right,subroot->right);
    }
    bool isSubtree(TreeNode* root, TreeNode* subroot) {
        if(root==NULL || subroot==NULL)return false;
        if(root->val==subroot->val){
            if(isid(root,subroot))return true;
        }
        return isSubtree(root->left,subroot)||isSubtree(root->right,subroot);
    }
};
```
<img width="1919" height="912" alt="image" src="https://github.com/user-attachments/assets/697cdb9f-127d-4fee-9af2-8fc0f9aa3b34" />  

**construct binary tree from preorder and inorder traversal**
```
class Solution {
public:
    unordered_map<int,int>m;
    int pi=0;
    TreeNode* build(vector<int>&preorder,int l,int r){
        if(l>r)return NULL;
        int rootval=preorder[pi++];
        TreeNode* node= new TreeNode(rootval);
        int mid=m[rootval];
        node->left=build(preorder,l,mid-1);
        node->right=build(preorder,mid+1,r);
        return node;
    }
    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) {
        for(int i=0;i<inorder.size();i++)m[inorder[i]]=i;
        return build(preorder,0,preorder.size()-1);
    }
};
```
<img width="1919" height="912" alt="image" src="https://github.com/user-attachments/assets/124001e7-2892-438a-84a1-4191a2f7362a" />
