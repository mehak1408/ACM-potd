**Power of 2**
```
class Solution {
public:
    bool isPowerOfTwo(int n) {
       if(n<=0)return false;
       return ((n & n-1)==0);
    }
};
```
<img width="1919" height="847" alt="image" src="https://github.com/user-attachments/assets/c90e66e1-65ab-4653-a2ae-b52682cdb80b" />  

**Combination sum**
```
class Solution {
public:
    set<vector<int>>s;
    void getans(vector<vector<int>>&ans, vector<int>&combin,int i,vector<int>&arr, int target){
        int n=arr.size();
        if(i==n || target<0)return;
        if(target==0){
            if(s.find(combin)==s.end()){
                s.insert(combin);
                ans.push_back(combin);
            }
        }
        combin.push_back(arr[i]);
        getans(ans,combin,i+1,arr,target-arr[i]);
        getans(ans,combin,i,arr,target-arr[i]);
        combin.pop_back();
        getans(ans,combin,i+1,arr,target);
    }
    vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
        vector<vector<int>>ans;
        vector<int>combin;
        getans(ans,combin,0,candidates,target);
        return ans;
    }
};
```
<img width="1919" height="912" alt="image" src="https://github.com/user-attachments/assets/1c4c3fe5-b0a8-4633-b089-b31480776d8e" />  

**Regualar expression matching**
```
class Solution {
public:
    bool solve(int i,int j,string &s, string &p,vector<vector<int>>&dp){
        if(dp[i][j]!=-1)return dp[i][j];
        if(j==p.size()){
            return dp[i][j]= i==s.size();
        }
        bool fm= ((i<s.size()) && (s[i]==p[j] || p[j]=='.'));
        if(j+1<p.size() && p[j+1]=='*'){
            return dp[i][j]= solve(i,j+2,s,p,dp) || (fm && solve(i+1,j,s,p,dp));
        }else{
            return dp[i][j]= fm && solve(i+1,j+1,s,p,dp);
        }
    }
    bool isMatch(string s, string p) {
        vector<vector<int>>dp(s.size()+1,vector<int>(p.size()+1,-1));
        return solve(0,0,s,p,dp);
    }
};
```
<img width="1919" height="856" alt="image" src="https://github.com/user-attachments/assets/f1b1bc83-85e7-4f66-b9a0-542e93fabc43" />
