**Find the town judge**
```
class Solution {
public:
    int findJudge(int n, vector<vector<int>>& trust) {
        vector<int>in(n+1,0),out(n+1,0);
        for(auto &e:trust){
            out[e[0]]++;
            in[e[1]]++;
        }
        for(int i=1;i<=n;i++){
            if(out[i]==0 && in[i]==n-1)return i;
        }
        return -1;
    }
};
```
<img width="1919" height="906" alt="image" src="https://github.com/user-attachments/assets/cc6f7c1f-a27c-480c-91f0-3de14d4fe04f" />  

**Course schedule**
```
class Solution {
public:
    bool canFinish(int V, vector<vector<int>>& edges) {
        vector<int>indegree(V,0);
        vector<vector<int>>adj(V);
        for(auto &e:edges){
            adj[e[0]].push_back(e[1]);
        }
        queue<int>q;
        for(int i=0;i<V;i++){
            for(auto it:adj[i]){
                indegree[it]++;
            }
        }
        for(int i=0;i<V;i++){
            if(indegree[i]==0){
                q.push(i);
            }
        }
        int cnt=0;
        while(!q.empty()){
            int node=q.front();
            q.pop();
            cnt++;
            for(auto &it:adj[node]){
                indegree[it]--;
                if(indegree[it]==0){
                    q.push(it);
                }
            }
        }
        if(cnt==V)return true;
        return false;
    }
};
```
<img width="1919" height="911" alt="image" src="https://github.com/user-attachments/assets/ece5f371-2ca3-489b-904d-2a8605b5a8e0" />  

**Reconstruct Itinerary**
```
class Solution {
public:
    unordered_map<string,multiset<string>>adj;
    vector<string>result;
    void dfs(string s){
        while(!adj[s].empty()){
            string next= *adj[s].begin();
            adj[s].erase(adj[s].begin());
            dfs(next);
        }
        result.push_back(s);
    }
    vector<string> findItinerary(vector<vector<string>>& tickets) {
        for(auto &e:tickets){
            adj[e[0]].insert(e[1]);
        }
        dfs("JFK");
        reverse(result.begin(),result.end());
        return result;
    }
};
```
<img width="1919" height="912" alt="image" src="https://github.com/user-attachments/assets/c65e2d38-f6fc-4fa6-af61-1030d036dd9c" />
