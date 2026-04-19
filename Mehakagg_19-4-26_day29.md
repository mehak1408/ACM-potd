**Fibonacci number**
```
class Solution {
public:
    int fib(int n) {
        int a=0;
        int b=1;
        for(int i=0;i<n;i++){
            int c=a+b;
            a=b;
            b=c;
        }
        return a;
    }
};
```
<img width="1917" height="926" alt="image" src="https://github.com/user-attachments/assets/03848372-7c4c-4905-b99f-ffc2375f6715" />  

**Subsets**
```
class Solution {
public:
    void help(vector<int>&nums,vector<vector<int>>&ans,vector<int>&combin,int idx){
        ans.push_back(combin);
        for(int i=idx;i<nums.size();i++){
            if(i>idx && nums[i]==nums[i-1])continue;
            combin.push_back(nums[i]);
            help(nums,ans,combin,i+1);
            combin.pop_back();
        }
    }
    vector<vector<int>> subsets(vector<int>& nums) {
        vector<vector<int>>ans;
        vector<int>combin;
        help(nums,ans,combin,0);
        return ans;
    }
};
```
<img width="1919" height="861" alt="image" src="https://github.com/user-attachments/assets/4abe6514-1c8d-42bf-a70b-924a245a47cc" />  

**N-queens**
```
class Solution {
public:
    bool issafe(vector<string>&board, int n,int row,int col){
        for(int i=0;i<n;i++){
            if(board[row][i]=='Q')return false;
        }
        for(int i=0;i<n;i++){
            if(board[i][col]=='Q')return false;
        }
        for(int i=row,j=col; i>=0 && j>=0;i--,j--){
            if(board[i][j]=='Q')return false;
        }
        for(int i=row,j=col; i>=0 && j<n;i--,j++){
            if(board[i][j]=='Q')return false;
        }
        return true;
    }
    void nqueen(vector<string>&board, vector<vector<string>>&ans, int n,int row){
        if(row==n){
            ans.push_back(board);
            return;
        }
        for(int i=0;i<n;i++){
            if(issafe(board,n,row,i)){
                board[row][i]='Q';
                nqueen(board,ans,n,row+1);
                board[row][i]='.';
            }
        }
    }
    vector<vector<string>> solveNQueens(int n) {
        vector<string>board(n,string(n,'.'));
        vector<vector<string>>ans;
        nqueen(board,ans,n,0);
        return ans;
    }
};
```
<img width="1919" height="853" alt="image" src="https://github.com/user-attachments/assets/789c0dcb-7881-490a-b64e-deb82272aab9" />
