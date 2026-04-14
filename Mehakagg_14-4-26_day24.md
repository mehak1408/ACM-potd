**Find center of star graph**
```
class Solution {
public:
    int findCenter(vector<vector<int>>& edges) {
        int n=edges.size()+1;
        vector<int>ans(n+1,0);
        for(auto &e:edges){
            ans[e[0]]++;
            ans[e[1]]++;
        }
        for(int i=1;i<=n;i++){
            if(ans[i]==n-1)return i;
        }
        return -1;
    }
};
```
<img width="1919" height="851" alt="image" src="https://github.com/user-attachments/assets/eb0e22b3-1c0f-48ee-b9bb-66555f4a7a19" />  

**Number of Provinces**
```
class Solution {
public:
    void dfs(int node, vector<vector<int>>&adj, vector<int>&vis){
        vis[node]=1;
        for(auto it:adj[node]){
            if(!vis[it]){
                dfs(it,adj,vis);
            }
        }
    }
    int findCircleNum(vector<vector<int>>& grid) {
        int n=grid.size();
        vector<vector<int>>adj(n);
        for(int i=0;i<n;i++){
            for(int j=0;j<n;j++){
                if(grid[i][j]==1){
                    adj[i].push_back(j);
                    adj[j].push_back(i);
                }
            }
        }
        vector<int>vis(n,0);
        int cnt=0;
        for(int i=0;i<n;i++){
            if(!vis[i]){
                cnt++;
                dfs(i,adj,vis);
            }
        }
        return cnt;
    }
};
```
<img width="1919" height="911" alt="image" src="https://github.com/user-attachments/assets/0af23ef5-cf24-4630-ae23-d15ed9886c99" />
