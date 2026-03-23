**subarray sum equals to k**
```
class Solution {
public:
    int subarraySum(vector<int>& nums, int k) {
        int n=nums.size();
        vector<int>ps(n);
        ps[0]=nums[0];
        for(int i=1;i<n;i++){
            ps[i]=ps[i-1]+nums[i];
        }
        unordered_map<int,int>m;
        int cnt=0;
        for(int i=0;i<nums.size();i++){
            if(ps[i]==k)cnt++;
            int val=ps[i]-k;
            if(m.find(val)!=m.end()){
                cnt+=m[val];
            }
            if(m.find(ps[i])==m.end()){
                m[ps[i]]=0;
            }
            m[ps[i]]++;
        }
        return cnt;
    }
};
```
<img width="1919" height="847" alt="image" src="https://github.com/user-attachments/assets/667e4ecf-0bd3-49cd-96e9-4af4e6a03f35" />
