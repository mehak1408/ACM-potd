**Best time to buy and sell stock**
```
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int bb=prices[0],maxp=0;
        for(int i=0;i<prices.size();i++){
            if(prices[i]>bb){
                maxp=max(maxp,prices[i]-bb);
            }
            bb=min(bb,prices[i]);
        }
        return maxp;
    }
};
```
<img width="1919" height="864" alt="image" src="https://github.com/user-attachments/assets/bac34cbd-cee1-4ad6-8d0f-b63684bc8deb" />
