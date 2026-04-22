**Longest increasing subsequence**
```
class Solution {
public:
    int lengthOfLIS(vector<int>& nums) {
        vector<int>tails;
        for (int num:nums) {
            auto it=lower_bound(tails.begin(), tails.end(), num);
            if (it==tails.end()) tails.push_back(num);
            else *it = num;
        }
        return tails.size();
    }
};
```
<img width="1919" height="892" alt="Screenshot 2026-04-22 230500" src="https://github.com/user-attachments/assets/2be73c16-f615-443f-afc6-721f20274001" />
