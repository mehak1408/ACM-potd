**Min cost climbing stairs**
```
class Solution {
public:
    int minCostClimbingStairs(vector<int>& cost) {
        int n=cost.size();
        int prev2=cost[0];
        int prev1=cost[1];
        for(int i=2;i<n;i++) {
            int curr=cost[i]+min(prev1, prev2);
            prev2=prev1;
            prev1=curr;
        }

        return min(prev1,prev2);
    }
};
```
<img width="1919" height="850" alt="image" src="https://github.com/user-attachments/assets/ea615799-806e-4c20-ba8a-1eeb1f4cf2c0" />  

**Partition equal subset sum**
```
class Solution {
public:
    bool canPartition(vector<int>& nums) {
        int totsum=0;
        for(int i:nums)totsum+=i;
        int n=nums.size();
        if(totsum%2!=0)return false;
        int k=totsum/2;
        vector<bool>prev(k+1,false);
        prev[0]=true;
        if(nums[0]<=k)prev[nums[0]]=true;
        for(int i=1;i<n;i++){
            vector<bool>curr(k+1,false);
            curr[0]=true;
            for(int j=1;j<=k;j++){
                bool nottake= prev[j];
                bool take=false;
                if(nums[i]<=j){
                    take=prev[j-nums[i]];
                }
                curr[j]=nottake||take;
            }
            prev=curr;
        }
        return prev[k];
    }
};
```
<img width="1919" height="903" alt="image" src="https://github.com/user-attachments/assets/0a4a4eb0-723f-4539-a018-02dd62da8652" />
