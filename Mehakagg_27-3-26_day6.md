**This file contains all 3 quetions of day 6**  
**Check if n and its double exist**
```
class Solution {
public:
    bool checkIfExist(vector<int>& arr) {
        for(int i=0;i<arr.size();i++){
            for(int j=0;j<arr.size();j++){
                if(((arr[i]==2*arr[j]) || (arr[j]==2*arr[i])) && i!=j){
                    return true;
                }
            }
        }
        return false;
    }
};
```
<img width="1919" height="904" alt="image" src="https://github.com/user-attachments/assets/1bdd67a0-a37c-4166-acbe-079b981bef55" />  

**Continuous subarray sum**
```
class Solution {
public:
    bool checkSubarraySum(vector<int>& nums, int k) {
        int p=0;
        unordered_map<int,int>m;
        m[0]=-1;
        for(int i=0;i<nums.size();i++){
            p+=nums[i];
            if(m.find(p%k)!=m.end()){
                if(i-m[p%k]>1){
                    return 1;
                }
            }else{
                m[p%k]=i;
            }
        }
        return 0;
    }
};
```
<img width="1919" height="858" alt="image" src="https://github.com/user-attachments/assets/07374b94-9093-4878-9dd8-110fbc184b0b" />  

**Candy**
```
class Solution {
public:
    int candy(vector<int>& ratings) {
        int n=ratings.size();
        vector<int>ans(n,1);
        for(int i=1;i<n;i++){
            if(ratings[i]>ratings[i-1]){
                ans[i]=ans[i-1]+1;
            }
        }
        int cnt=0;
        for(int i=n-1;i>0;i--){
            if(ratings[i-1]>ratings[i]){
                ans[i-1]=max(ans[i]+1,ans[i-1]);
            }
            cnt+=ans[i-1];
        }
        return cnt+ans[n-1];
    }
};
```
<img width="1919" height="859" alt="image" src="https://github.com/user-attachments/assets/5900f764-e3d4-4ec5-a2bc-9bfb6dfb93a3" />
