**This file contains all 3 questions of day 5**  
**Move Zeroes**
```
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        int i=0;
        for(int j=0;j<nums.size();j++){
            if(nums[j]!=0){
                swap(nums[i],nums[j]);
                i++;
            }
        }
    }
};
```
<img width="1919" height="916" alt="image" src="https://github.com/user-attachments/assets/c2b41f36-1e0d-4262-9934-a954f229b496" />  

**Product of array except self**
```
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        int n=nums.size();
        vector<int>ans(n,1);
        for(int i=1;i<n;i++){
            ans[i]=ans[i-1]*nums[i-1];
        }
        int suffix=1;
        for(int i=n-2;i>=0;i--){
            suffix*=nums[i+1];
            ans[i]*=suffix;
        }
        return ans;
    }
};
```
<img width="1919" height="852" alt="image" src="https://github.com/user-attachments/assets/b5a2da60-f031-4138-91a1-1b737ee44c21" />  

**Sliding window maximum**
```
class Solution {
public:
    vector<int> maxSlidingWindow(vector<int>& nums, int k) {
        deque<int>dq;
        vector<int>res;
        int n=nums.size();
        for(int i=0;i<k;i++){
            while(dq.size()>0 && nums[dq.back()]<=nums[i])dq.pop_back();
            dq.push_back(i);
        }
        for(int i=k;i<n;i++){
            res.push_back(nums[dq.front()]);
            while(dq.size()>0 && dq.front()<=i-k)dq.pop_front();
            while(dq.size()>0 && nums[dq.back()]<=nums[i])dq.pop_back();
            dq.push_back(i);
        }
        res.push_back(nums[dq.front()]);
        return res;
    }
};
```
<img width="1919" height="854" alt="image" src="https://github.com/user-attachments/assets/589dfe72-7671-42ba-b6e1-ca2dec220889" />
