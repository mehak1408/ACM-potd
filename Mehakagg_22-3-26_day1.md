```
Solution contains removing duplicates from a sorted array where a pointer which is i is used to track non duplicate elements by swapping it with elements occuring at jth position and satisfying condition. This algorithm works with
Time complexity= O(n)
space complexity= O(1)

```
```
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        if(nums.empty())return 0;
        int i=1;
        for(int j=0;j<nums.size();j++){
            if(nums[i-1]!=nums[j]){
                nums[i++]=nums[j];
            }
        }
        return i; 
    }
};
```

<img width="1913" height="849" alt="image" src="https://github.com/user-attachments/assets/8dce1e4d-5741-465b-b629-7d3078ca797a" />
