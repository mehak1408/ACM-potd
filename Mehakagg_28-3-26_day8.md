**This file contains all 3 questions of day 8**  
**Reverse Linked list**  
```
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        ListNode* prev=NULL;
        ListNode* curr=head;
        ListNode* next=NULL;
        while(curr!=NULL){
            next=curr->next;
            curr->next=prev;
            prev=curr;
            curr=next;
        }
        return prev;
    }
};
```
<img width="1919" height="857" alt="image" src="https://github.com/user-attachments/assets/d3172377-c3aa-4a0e-a408-8678fd996675" />  

**Remove nth node from end of the list**
```
class Solution {
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        if(head==NULL)return NULL;
        int c=0;
        ListNode* temp=head;
        while(temp!=NULL){
            c++;
            temp=temp->next;
        }
        if(c==n){
            ListNode* newhead=head->next;
            delete head;
            return newhead;
        }
        temp=head;
        for(int i=1;i<c-n;i++){
            temp=temp->next;
        }
        ListNode* ne=temp->next;
        temp->next=temp->next->next;
        delete ne;
        return head;
    }
};
```
<img width="1919" height="816" alt="image" src="https://github.com/user-attachments/assets/c7b73984-84ca-4cfa-8529-f2335238ffbb" />  

**Reverse nodes in k-group**
```
class Solution {
public:
    ListNode* reverseKGroup(ListNode* head, int k) {
        ListNode* curr=head;
        for(int i=0;i<k;i++){
            if(!curr)return head;
            curr=curr->next;
        }
        curr=head;
        ListNode* prev=NULL;
        for(int i=0;i<k;i++){
            ListNode* next=curr->next;
            curr->next=prev;
            prev=curr;
            curr=next;
        }
        head->next=reverseKGroup(curr,k);
        return prev;
    }
};
```
<img width="1919" height="861" alt="image" src="https://github.com/user-attachments/assets/0e3672f0-79bb-446c-a082-f4d47c4865d6" />
