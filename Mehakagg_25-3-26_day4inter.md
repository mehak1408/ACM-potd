**Two sum II- Input array is sorted**
```
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        int i=0,j=nums.size()-1;
        while(i<j){
            int sum=nums[i]+nums[j];
            if(sum==target){
                return {i+1,j+1};
            }else if(sum<target)i++;
            else{
                j--;
            }
        }
        return {};
    }
};
```
<img width="1919" height="850" alt="image" src="https://github.com/user-attachments/assets/d350e8f9-cc56-4531-ab5a-c25e9a61a8e6" />
