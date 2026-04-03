**This file contains all 3 questions of day 13**  
**Intersection of two list**  
```
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        ListNode* t1=headA;
        ListNode* t2=headB;
        while(t1!=t2){
            t1=(t1==NULL)?headB:t1->next;
            t2=(t2==NULL)?headA:t2->next;
        }
        return t1;
    }
};
```
<img width="1919" height="855" alt="image" src="https://github.com/user-attachments/assets/6634b8c7-9105-4a8f-8649-d932e1f452bc" />  

**Remove duplicates from sorted list II**  
```
class Solution {
public:
    ListNode* deleteDuplicates(ListNode* head) {
        ListNode* dummy=new ListNode(0);
        dummy->next=head;
        ListNode* prev=dummy;
        ListNode* curr=head;
        while(curr!=NULL){
            if(curr->next && curr->val==curr->next->val){
                while(curr->next && curr->val==curr->next->val){
                    curr=curr->next;
                }
                prev->next=curr->next;
            }
            else{
                prev=prev->next;
            }
            curr=curr->next;
        }
        return dummy->next;
    }
};
```
<img width="1919" height="909" alt="image" src="https://github.com/user-attachments/assets/ff545235-d744-48ce-9774-1ee085797450" />  

**Search in a rotated sorted array**  
```
class Solution {
public:
    int search(vector<int>& arr, int target) {
        int st=0, end=arr.size()-1;
        while(st<=end){
            int mid= st+(end-st)/2;
            if(arr[mid]==target)return mid;
            if(arr[st]<=arr[mid]){
                if(arr[st]<=target && target<=arr[mid]){
                    end=mid-1;
                }else{
                    st=mid+1;
                }
            }else{
                if(arr[mid]<=target && target<=arr[end]){
                    st=mid+1;
                }else{
                    end=mid-1;
                }
            }
        }
        return -1;
    }
};
```
<img width="1919" height="860" alt="image" src="https://github.com/user-attachments/assets/110949e0-3d1f-4195-8160-ece1e456ff1c" />
