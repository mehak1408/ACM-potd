**Merge two sorted list**
```
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* h1, ListNode* h2) {
        if(h1==NULL || h2==NULL){
            return h1==NULL?h2:h1;
        }
        if(h1->val<=h2->val){
            h1->next= mergeTwoLists(h1->next,h2);
            return h1;
        }else{
            h2->next= mergeTwoLists(h1,h2->next);
            return h2;
        }
    }
};
```
<img width="1919" height="921" alt="image" src="https://github.com/user-attachments/assets/70f84fe0-ad8d-4597-ad1f-3a89d057e095" />  

**Sort list**
```
class Solution {
public:
    ListNode* merge(ListNode* l1,ListNode* l2){
        ListNode* dummy= new ListNode(-1);
        ListNode* temp=dummy;
        while(l1!=NULL && l2!=NULL){
            if(l1->val<l2->val){
                temp->next=l1;
                temp=l1;
                l1=l1->next;
            }else{
                temp->next=l2;
                temp=l2;
                l2=l2->next;
            }
        }
        if(l1){
            temp->next=l1;
        }else{
            temp->next=l2;
        }
        return dummy->next;
    }
    ListNode* findm(ListNode* head){
        ListNode* slow=head;
        ListNode* fast= head->next;
        while(fast!=NULL && fast->next!=NULL){
            slow=slow->next;
            fast=fast->next->next;
        }
        return slow;
    }
    ListNode* sortList(ListNode* head) {
        if(head==NULL || head->next==NULL){
            return head;
        }
        ListNode* mid= findm(head);
        ListNode* right= mid->next;
        mid->next=NULL;
        ListNode* left= head;

        left= sortList(left);
        right= sortList(right);
        return merge(left,right);
    }
};
```
<img width="1919" height="851" alt="image" src="https://github.com/user-attachments/assets/f92a601d-2216-471f-9cd8-2381f36d433f" />
