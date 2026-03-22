**Trapping rainwater problem**

```
class Solution {
public:
    int trap(vector<int>& height) {
        int ans=0,l=0,r=height.size()-1,maxl=0,maxr=0;
        for(int i=0;i<height.size();i++){
            maxl=max(maxl,height[l]);
            maxr=max(maxr,height[r]);
            if(maxl<maxr){
                ans+=(maxl-height[l++]);
            }else{
                ans+=(maxr-height[r--]);
            }
        }
        return ans;
    }
};
```
<img width="1919" height="910" alt="image" src="https://github.com/user-attachments/assets/ce7005b8-e398-42c5-b672-ed6e63c09edb" />
