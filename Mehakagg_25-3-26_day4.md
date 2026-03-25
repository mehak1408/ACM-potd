**Missing Number**
```
class Solution {
public:
    int missingNumber(vector<int>& nums) {
       int n=nums.size();
       set<int>s(nums.begin(),nums.end());
       for(int i=0;i<=n;i++){
        if(s.find(i)==s.end()){
            return i;
        }
       }
       return -1;
    }
};
```
<img width="1919" height="921" alt="image" src="https://github.com/user-attachments/assets/05d77ccc-d5a7-45ff-b195-7dff893f0e82" />
