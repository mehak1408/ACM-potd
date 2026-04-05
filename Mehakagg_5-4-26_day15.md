**Valid parenthesis**  
```
class Solution {
public:
    bool isValid(string str) {
        stack<char>st;
        for(int i=0;i<str.length();i++){
            if(str[i]=='(' || str[i]=='{' || str[i]=='[')st.push(str[i]);
            else{
                if(st.size()==0)return false;
                if((st.top()=='(' && str[i]==')') || (st.top()=='{' && str[i]=='}') || (st.top()=='[' && str[i]==']'))st.pop();
                else return false;
            }
        }
        return st.size()==0;
    }
};
```
<img width="1919" height="856" alt="image" src="https://github.com/user-attachments/assets/b7ea1257-7f69-4b5f-9a9c-d38e5339ccfc" />  

**Min stack**
```
class MinStack {
public:
    stack<pair<int,int>>s;
    MinStack() {
        
    }
    
    void push(int val) {
        if(s.empty()){
            s.push({val,val});
        }else{
            int minv= min(val,s.top().second);
            s.push({val,minv});
        }
    }
    
    void pop() {
        s.pop();
    }
    
    int top() {
        return s.top().first;
    }
    
    int getMin() {
        return s.top().second;
    }
};
```
<img width="1919" height="849" alt="image" src="https://github.com/user-attachments/assets/dc8edb33-897b-401e-9e86-04309485cbab" />  

**Maximal Rectangle**
```
class Solution {
public:
    int helper(vector<int>&heights){
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
        int maxarea=0;
        for(int i=0;i<n;i++){
            maxarea= max(maxarea,heights[i]*(right[i]-left[i]-1));
        }
        return maxarea;
    }
    int maximalRectangle(vector<vector<char>>& matrix) {
        if(matrix.empty())return 0;
        int n=matrix.size(),m=matrix[0].size();
        vector<vector<int>>psum(n,vector<int>(m,0));
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(matrix[i][j]=='1'){
                    psum[i][j]=(i==0?1:psum[i-1][j]+1);
                }
            }
        }
        int maxa=0;
        for(int i=0;i<n;i++){
            maxa= max(maxa,helper(psum[i]));
        }
        return maxa;
    }
};
```
<img width="1919" height="849" alt="image" src="https://github.com/user-attachments/assets/9275598f-b908-4e1e-891f-8c7e2941f39b" />
