**Sort colors**
```
class Solution {
public:
    void sortColors(vector<int>& nums) {
        int low=0,mid=0,high=nums.size()-1;
        while(mid<=high){
            if(nums[mid]==0){
                swap(nums[low++],nums[mid++]);
            }else if(nums[mid]==1){
                mid++;
            }else{
                swap(nums[mid],nums[high--]);
            }
        }
    }
};
```
<img width="1919" height="812" alt="image" src="https://github.com/user-attachments/assets/1bf029b8-eb6a-4800-96b0-1bc2b5553814" />
