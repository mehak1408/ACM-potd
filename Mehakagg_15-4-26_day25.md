**Maximum depth of binary tree**
```
class Solution {
public:
    int maxDepth(TreeNode* root) {
        if(root==NULL)return 0;
        int lh=maxDepth(root->left);
        int rh=maxDepth(root->right);
        return max(lh,rh)+1;
    }
};
```
<img width="1919" height="851" alt="image" src="https://github.com/user-attachments/assets/adf17564-16f6-4be3-a1ae-2b1ac961c0d4" />  

**Binary tree level order traversal**
```
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
        if(root==NULL)return {};
        queue<TreeNode*>q;
        q.push(root);
        vector<vector<int>>ans;
        while(!q.empty()){
            int size= q.size();
            vector<int>level;
            for(int i=0;i<size;i++){
                TreeNode* curr=q.front();
                q.pop();
                level.push_back(curr->val);
                if(curr->left)q.push(curr->left);
                if(curr->right)q.push(curr->right);
            }
            ans.push_back(level);
        }
        return ans;
    }
};
```
<img width="1919" height="908" alt="image" src="https://github.com/user-attachments/assets/741996da-192b-409d-873c-3f2749072244" />  

**Binary tree maximum path sum**
```
class Solution {
public:
    int diam(TreeNode* root, int &maxsum){
        if(root==NULL)return 0;
        int lh=max(0,diam(root->left,maxsum));
        int rh=max(0,diam(root->right,maxsum));
        maxsum=max(lh+rh+root->val,maxsum);
        return max(lh,rh)+root->val;
    }
    int maxPathSum(TreeNode* root) {
        int maxsum=INT_MIN;
        diam(root,maxsum);
        return maxsum;
    }
};
```
<img width="1919" height="845" alt="image" src="https://github.com/user-attachments/assets/1adf3c4f-5d86-46ac-ad0a-fc4566d643f7" />
