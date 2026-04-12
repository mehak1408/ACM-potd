**Flood Fill**
```
class Solution {
public:
    void dfs(vector<vector<int>>& image, int r, int c, int oldColor, int newColor) {
        int n = image.size();
        int m = image[0].size();
        image[r][c] = newColor;
        int dr[] = {-1,0,1,0};
        int dc[] = {0,1,0,-1};
        for(int i=0; i<4; i++) {
            int nr = r + dr[i], nc = c + dc[i];
            if(nr>=0 && nr<n && nc>=0 && nc<m && image[nr][nc] == oldColor) {
                dfs(image, nr, nc, oldColor, newColor);
            }
        }
    }
    vector<vector<int>> floodFill(vector<vector<int>>& image, int sr, int sc, int color) {
        int oldColor = image[sr][sc];
        if(oldColor == color) return image; 
        dfs(image, sr, sc, oldColor, color);
        return image;
    }
};
```
<img width="1918" height="911" alt="image" src="https://github.com/user-attachments/assets/5721172f-2179-47f4-a014-c51ff2ebd233" />  

**Number of Islands**
```
class Solution {
public:
    void dfs(int row,int col,vector<vector<int>>&vis, vector<vector<char>>&grid){
        vis[row][col]=1;
        int n=grid.size();
        int m=grid[0].size();
        int dr[]={0,-1,0,1};
        int dc[]={-1,0,1,0};
        for(int i=0;i<4;i++){
            int nrow=row+dr[i];
            int ncol=col+dc[i];
            if(nrow<n && nrow>=0 && ncol<m && ncol>=0 && !vis[nrow][ncol] && grid[nrow][ncol]=='1'){
                dfs(nrow,ncol,vis,grid);
            }
        }
    }
    int numIslands(vector<vector<char>>& grid) {
        int n=grid.size();
        int m=grid[0].size();
        vector<vector<int>>vis(n,vector<int>(m,0));
        int cnt=0;
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(grid[i][j]=='1' && !vis[i][j]){
                    cnt++;
                    dfs(i,j,vis,grid);
                }
            }
        }
        return cnt;
    }
};
```
<img width="1919" height="905" alt="image" src="https://github.com/user-attachments/assets/a51fdc64-713d-4284-9918-58c647b01137" />  

**Cheapest flights within k stops**
```
class Solution {
public:
    int findCheapestPrice(int n, vector<vector<int>>& edges, int src, int dst, int k) {
        vector<vector<pair<int,int>>>adj(n);
        for(auto &e:edges){
            adj[e[0]].push_back({e[1],e[2]});
        }
        queue<pair<int,pair<int,int>>>q;
        //stops,node,cost
        vector<int>dist(n,1e9);
        q.push({0,{src,0}});
        dist[src]=0;
        while(!q.empty()){
            auto it=q.front();
            q.pop();
            int stop=it.first;
            int node= it.second.first;
            int cost= it.second.second;
            if(stop>k)continue;
            for(auto it:adj[node]){
                int dest=it.first;
                int price=it.second;
                if(cost+price<dist[dest] && stop<=k){
                    dist[dest]=cost+price;
                    q.push({stop+1,{dest,cost+price}});
                }
            }
        }
        if(dist[dst]==1e9)return -1;
        return dist[dst];
    }
};
```
<img width="1919" height="848" alt="image" src="https://github.com/user-attachments/assets/fb809a65-7cc2-4416-a6d2-03f41617005f" />
