**This file contains all 3 questions of day 7**  
**Rotate Array**
```
class Solution {
public:
    void rotate(vector<int>& nums, int k) {
        int n= nums.size();
        k%=n;
        reverse(nums.begin(),nums.end());
        reverse(nums.begin(),nums.begin()+k);
        reverse(nums.begin()+k,nums.end());
    }
};
```
<img width="1919" height="854" alt="image" src="https://github.com/user-attachments/assets/7dd80625-6898-4706-98bb-f5380decc51e" />  

**Increasing triplet subsequence**
```
class Solution {
public:
    bool increasingTriplet(vector<int>& nums) {
        if(nums.size()<3)return false;
        int first=INT_MAX;
        int second=INT_MAX;
        for(int i:nums){
            if(i<=first)first=i;
            else if(i<=second)second=i;
            else return true;
        }
        return false;
    }
};
```
<img width="1919" height="851" alt="image" src="https://github.com/user-attachments/assets/5c6da051-518b-460f-9708-c1a09d925a89" />  

**Maximum score of good subarray**
```
class Solution {
public:
    int maximumScore(vector<int>& nums, int k) {
        int n=nums.size();
        int l=k,r=k;
        int minv=nums[k];
        int maxs=nums[k];
        while(l>0 || r<n-1){
            if(l==0)r++;
            else if(r==n-1)l--;
            else if(nums[l-1]>nums[r+1])l--;
            else r++;
            minv=min(minv,min(nums[l],nums[r]));
            maxs=max(maxs,minv*(r-l+1));
        }
        return maxs;
    }
};
```
<img width="1919" height="842" alt="image" src="https://github.com/user-attachments/assets/ef66bd54-0c8f-43ea-8286-843330326b58" />  
