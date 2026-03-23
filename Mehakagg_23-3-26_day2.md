**Two sum problem**
```
class Solution {
public:
    vector<int> twoSum(vector<int>& arr, int target) {
        unordered_map<int,int> m;
        vector<int> ans;
        for(int i=0; i<arr.size(); i++){
            int first= arr[i];
            int sec= target-first;
            if(m.find(sec)!=m.end()){
                ans.push_back(i);
                ans.push_back(m[sec]);
                break;
            }
            m[first]=i;
        }
        return ans;
    }
};
```
<img width="1919" height="867" alt="image" src="https://github.com/user-attachments/assets/ac0b90dd-9ade-4018-9717-da05c8ef8242" />
