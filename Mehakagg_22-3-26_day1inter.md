**Three sum problem**
```
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        int n=nums.size();
        vector<vector<int>>ans;
        sort(nums.begin(),nums.end());
        for(int i=0;i<n;i++){
            if(i>0 && nums[i]==nums[i-1])continue;
            else{
                int j=i+1,k=n-1;
                while(j<k){
                    int sum=nums[i]+nums[j]+nums[k];
                    if(sum>0)k--;
                    else if(sum<0)j++;
                    else{
                        ans.push_back({nums[i],nums[j++],nums[k--]});
                        while(j<k && nums[j]==nums[j-1])j++;
                    }
                }
            }
        }
        return ans;
    }
};
```
<img width="1919" height="864" alt="image" src="https://github.com/user-attachments/assets/384343f2-dd13-410e-b7e2-47f04c6442d8" />
