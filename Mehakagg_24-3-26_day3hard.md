**Largest rectangle in histogram**
```
class Solution {
public:
    int largestRectangleArea(vector<int>& heights) {
        int n=heights.size();
        vector<int>right(n,0),left(n,0);
        stack<int>s;
        for(int i=n-1;i>=0;i--){
            while(!s.empty() && heights[s.top()]>=heights[i])s.pop();
            right[i]=s.empty()?n:s.top();
            s.push(i);
        }
        while(!s.empty())s.pop();
        for(int i=0;i<n;i++){
            while(!s.empty() && heights[s.top()]>=heights[i])s.pop();
            left[i]=s.empty()?-1:s.top();
            s.push(i);
        }
        int ans=0;
        for(int i=0;i<n;i++){
            int currarea= heights[i]*(right[i]-left[i]-1);
            ans=max(ans,currarea);
        }
        return ans;
    }
};
```
<img width="1919" height="867" alt="image" src="https://github.com/user-attachments/assets/915e4198-d06b-43f0-9571-6b833b56d3dd" />
