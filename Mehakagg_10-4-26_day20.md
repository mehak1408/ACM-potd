**Remove outermost parenthesis**
```
class Solution {
public:
    string removeOuterParentheses(string s) {
        string ans="";
        stack<char>st;
        string p="";
        for(int i=0; i<s.length();i++){
            if(s[i]=='('){
                st.push(s[i]);
                p+=s[i];
            }else{
                st.pop();
                p+=s[i];
            }
            if(st.empty()){
                string trim= p.substr(1,p.length()-2);
                ans+=trim;
                p="";
            }
        }
        return ans;
    }
};
```
<img width="1919" height="845" alt="image" src="https://github.com/user-attachments/assets/bf92677a-bfa7-4f25-83f9-f9dc214db361" />
