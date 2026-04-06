**Implement queue using stacks**  
```
class MyQueue {
public:
    MyQueue() {
        
    }
    stack<int>s1;
    stack<int>s2;
    void push(int x) {
        while(!s1.empty()){
            s2.push(s1.top());
            s1.pop();
        }
        s1.push(x);
        while(!s2.empty()){
            s1.push(s2.top());
            s2.pop();
        }
    }
    
    int pop() {
        int x=s1.top();
        s1.pop();
        return x;
    }
    
    int peek() {
        return s1.top();
    }
    
    bool empty() {
        return s1.empty();
    }
};
```
<img width="1919" height="850" alt="image" src="https://github.com/user-attachments/assets/2ef031d5-450d-4ec9-a187-34d6c8459795" />  

**Daily temperatures**  
```
class Solution {
public:
    vector<int> dailyTemperatures(vector<int>& arr) {
        int n=arr.size();
        vector<int>ans(n,0);
        stack<int>s;
        for(int i=n-1;i>=0;i--){
            while(!s.empty() && arr[s.top()]<=arr[i])s.pop();
            ans[i]=s.empty()?0:s.top()-i;
            s.push(i);
        }
        return ans;
    }
};
```
<img width="1919" height="857" alt="image" src="https://github.com/user-attachments/assets/e35c049c-f7c8-49c5-935d-0ca80e4f8cb9" />  

**Trapping Rainwater II**  
```
class Solution {
public:
    int trapRainWater(vector<vector<int>>& grid) {
        int m=grid.size();
        int n=grid[0].size();
        vector<vector<int>>vis(m,vector<int>(n,0));
        priority_queue<pair<int,pair<int,int>>,vector<pair<int,pair<int,int>>>,greater<pair<int,pair<int,int>>>>q;
        for(int i=0;i<m;i++){
            q.push({grid[i][0],{i,0}});
            q.push({grid[i][n-1],{i,n-1}});
            vis[i][0]=1;
            vis[i][n-1]=1;
        }
        for(int i=0;i<n;i++){
            q.push({grid[0][i],{0,i}});
            q.push({grid[m-1][i],{m-1,i}});
            vis[0][i]=1;
            vis[m-1][i]=1;
        }
        int water=0;
        int dr[]={0,-1,0,1};
        int dc[]={-1,0,1,0};
        while(!q.empty()){
            auto it=q.top();
            q.pop();
            int h=it.first;
            int r=it.second.first;
            int c=it.second.second;
            for(int i=0;i<4;i++){
                int nr=r+dr[i];
                int nc=c+dc[i];
                if(nr>=0 && nr<m && nc>=0 && nc<n && !vis[nr][nc]){
                    vis[nr][nc]=1;
                    water+=max(0,h-grid[nr][nc]);
                    q.push({max(h,grid[nr][nc]),{nr,nc}});
                }
            }
        }
        return water;
    }
};
```
<img width="1919" height="852" alt="image" src="https://github.com/user-attachments/assets/e2705a51-09a5-4d1a-a725-cac719d98997" />
