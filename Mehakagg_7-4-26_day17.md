**Implement stack using queues**  
```
class MyStack {
public:
    MyStack() {
        
    }
    queue<int>q1;
    queue<int>q2;
    void push(int x) {
        while(!q1.empty()){
            q2.push(q1.front());
            q1.pop();
        }
        q1.push(x);
        while(!q2.empty()){
            q1.push(q2.front());
            q2.pop();
        }
    }
    
    int pop() {
       int a=q1.front();
       q1.pop();
       return a;
    }
    
    int top() {
        return q1.front();
    }
    
    bool empty() {
        return q1.empty();
    }
};
```
<img width="1919" height="843" alt="image" src="https://github.com/user-attachments/assets/2fe04701-abef-4db6-bf15-92db04af4a64" />  

**Next greater element I**  
```
class Solution {
public:
    vector<int> nextGreaterElement(vector<int>& nums1, vector<int>& nums2) {
        stack<int>s;
        unordered_map<int,int>m;
        int n=nums2.size();
        for(int i=n-1;i>=0;i--){
            while(!s.empty() && nums2[s.top()]<=nums2[i])s.pop();
            m[nums2[i]]=s.empty()?-1:nums2[s.top()];
            s.push(i);
        }
        vector<int>ans;
        for(int i=0;i<nums1.size();i++){
            ans.push_back(m[nums1[i]]);
        }
        return ans;
    }
};
```
<img width="1919" height="911" alt="image" src="https://github.com/user-attachments/assets/ca9d8e0b-3eaf-40fe-9acb-e8adc65c8ff4" />  

**Remove duplicate letters**  
```
class Solution {
public:
    string removeDuplicateLetters(string s) {
        vector<int>li(26,0);
        for(int i=0;i<s.size();i++){
            li[s[i]-'a']=i;
        }
        vector<bool>seen(26,false);
        stack<char>st;
        for(int i=0;i<s.size();i++){
            int curr=s[i]-'a';
            if(seen[curr])continue;
            while(!st.empty() && st.top()>s[i] && i<li[st.top()-'a']){
                seen[st.top()-'a']=false;
                st.pop();
            }
            seen[curr]=true;
            st.push(s[i]);
        }
        string ans="";
        while(!st.empty()){
            ans+=st.top();
            st.pop();
        }
        reverse(ans.begin(),ans.end());
        return ans;
    }
};
```
<img width="1919" height="906" alt="image" src="https://github.com/user-attachments/assets/da0c0e38-af96-45b6-b851-34c412694069" />
