**First Missing positive**
```
class Solution {
public:
    int firstMissingPositive(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        int tar=1;
        for(int i:nums){
            if(i==tar){
                tar++;
            }else if(i>tar){
                return tar;
            }
        }
        return tar;
    }
};
```
<img width="1916" height="857" alt="image" src="https://github.com/user-attachments/assets/a0c922f9-7877-42d9-a4d6-aaa446a931fc" />
