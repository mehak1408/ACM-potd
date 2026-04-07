**Remove all adjacent duplicates from string**
```
class Solution {
public:
    string removeDuplicates(string s) {
        stack<char>st;
        for(int i=0;i<s.size();i++){
            if(!st.empty() && st.top()==s[i])st.pop();
            else st.push(s[i]);
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
<img width="1919" height="851" alt="image" src="https://github.com/user-attachments/assets/dbfc8fa1-2843-4d60-b2ed-5d872d6464f8" />  

**Next greater element II**
```
class Solution {
public:
    vector<int> nextGreaterElements(vector<int>& nums) {
        stack<int>s;
        int n=nums.size();
        vector<int>ans(n,0);
        for(int i=2*n-1;i>=0;i--){
            while(!s.empty() && nums[s.top()]<=nums[i%n])s.pop();
            ans[i%n]=s.empty()?-1:nums[s.top()];
            s.push(i%n);
        }
        return ans;
    }
};
```
<img width="1919" height="850" alt="image" src="https://github.com/user-attachments/assets/4d8b4561-0ef0-46a4-a08e-8a87dc21aeb6" />  

**Minimum cost tree from leaf values**  
```
class Solution {
public:
    int mctFromLeafValues(vector<int>& arr) {
        stack<int>s;
        s.push(INT_MAX);
        int n=arr.size();
        int ans=0;
        for(int i:arr){
            while(s.top()<=i){
                int m=s.top();
                s.pop();
                ans+=m*min(s.top(),i);
            }
            s.push(i);
        }
        while(s.size()>2){
            int m=s.top();
            s.pop();
            ans+=m*s.top();
        }
        return ans;
    }
};
```
<img width="1919" height="852" alt="image" src="https://github.com/user-attachments/assets/8a7cfc3a-ea0c-43fe-ac61-60479b938790" />
