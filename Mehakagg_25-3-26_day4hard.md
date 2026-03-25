**Count of smaller numbers after self**
```
class Solution {
public:
    vector<int>ans;
    void merge(vector<pair<int,int>>&arr,int st,int end,int mid){
        vector<pair<int,int>> temp;
        int i=st,j=mid+1;
        int cnt=0;
        while(i<=mid && j<=end){
            if(arr[j].first<arr[i].first){
                temp.push_back(arr[j++]);
                cnt++;
            }else{
                ans[arr[i].second]+=cnt;
                temp.push_back(arr[i++]);
            }
        }
        while(i<=mid){
            ans[arr[i].second]+=cnt;
            temp.push_back(arr[i++]);
        }
        while(j<=end){
            temp.push_back(arr[j++]);
        }
        for(int idx=0;idx<temp.size();idx++){
            arr[idx+st]=temp[idx];
        }
    }
    void mergesort(vector<pair<int,int>>&arr,int st,int end){
        if(st>=end)return;
        int mid= st+(end-st)/2;
        mergesort(arr,st,mid);
        mergesort(arr,mid+1,end);
        merge(arr,st,end,mid);
    }
    vector<int> countSmaller(vector<int>& nums) {
        int n=nums.size();
        ans.resize(n,0);
        vector<pair<int,int>>arr;
        for(int i=0;i<n;i++){
            arr.push_back({nums[i],i});
        }
        mergesort(arr,0,n-1);
        return ans;
    }
};
```
<img width="1915" height="909" alt="image" src="https://github.com/user-attachments/assets/237ac38c-4680-4aab-b27a-232756cf9fcb" />
