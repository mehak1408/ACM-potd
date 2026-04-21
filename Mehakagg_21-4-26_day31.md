**Climbing stairs**
```
class Solution {
public:
    int climbStairs(int n) {
        int a=0;
        int b=1;
        for(int i=0;i<n;i++){
            int curr =a+b;
            a=b;
            b=curr;
        }
        return b;
    }
};
```
<img width="1919" height="850" alt="Screenshot 2026-04-21 223031" src="https://github.com/user-attachments/assets/6eb36653-7727-4468-b213-6b0c43dd3a5c" />  

**Generate parenthesis**
```
class Solution {
public:
    void solve(int sb, int cb, string cur, int n, vector<string>&res){
        if(cur.length()==2*n){
            res.push_back(cur);
            return;
        }
        if(sb<n){
            solve(sb+1,cb,cur+'(',n,res);
        }
        if(cb<sb){
            solve(sb,cb+1,cur+')',n,res);
        }
    }
    vector<string> generateParenthesis(int n) {
        vector<string>res;
        solve(0,0,"",n,res);
        return res;
    }
};
```
<img width="1919" height="864" alt="image" src="https://github.com/user-attachments/assets/2e40cc2e-cafe-4946-8737-29058cdbc8e9" />  

**sudoko solver**
```
class Solution {
public:
    bool issafe(vector<vector<char>>&board,int row,int col,char dig){
        for(int i=0;i<9;i++){
            if(board[row][i]==dig)return false;
        }
        for(int i=0;i<9;i++){
            if(board[i][col]==dig)return false;
        }
        int sr=(row/3)*3;
        int sc=(col/3)*3;
        for(int i=sr;i<=sr+2;i++){
            for(int j=sc;j<=sc+2;j++){
                if(board[i][j]==dig)return false;
            }
        }
        return true;
    }
    bool helper(vector<vector<char>>& board,int row, int col){
        if(row==9)return true;
        int nextrow=row, nextcol=col+1;
        if(nextcol==9){
            nextrow=row+1;
            nextcol=0;
        }
        if(board[row][col]!='.')return helper(board,nextrow,nextcol);
        for(char i='1';i<='9';i++){
            if(issafe(board,row,col,i)){
                board[row][col]=i;
                if(helper(board,nextrow,nextcol))return true;
                board[row][col]='.';
            }
        }
        return false;
    }
    void solveSudoku(vector<vector<char>>& board) {
        helper(board,0,0);
    }
};
```
<img width="1919" height="856" alt="image" src="https://github.com/user-attachments/assets/ef8f7c18-dbb0-4503-b0a1-f6a361996c37" />
