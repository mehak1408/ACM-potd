**Palindrome linked list**  
```
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        ListNode* prev= NULL;
        ListNode* curr= head;
        ListNode* next= NULL;
        while(curr!=NULL){
            next=curr->next;
            curr->next= prev;

            prev=curr;
            curr=next;
        }
        return prev;
    }
    bool isPalindrome(ListNode* head) {
        ListNode* slow = head;
        ListNode* fast = head;
        while (fast->next && fast->next->next) {
            slow = slow->next;
            fast = fast->next->next;
        }
        ListNode* temp = reverseList(slow->next);
        while(temp!=NULL){
            if(temp->val!=head->val){
                return false;
            }
            temp=temp->next;
            head=head->next;
        }
        return true;
    }
};
```
<img width="1919" height="862" alt="image" src="https://github.com/user-attachments/assets/dd2d956d-4771-4743-8a3b-4ae82117d7d9" />  

**Swap nodes in pairs**  
```
class Solution {
public:
    ListNode* swapPairs(ListNode* head) {
        if(head==NULL || head->next==NULL)return head;
        ListNode* dummy= new ListNode(0);
        dummy->next=head;
        ListNode* prev=dummy;
        while(prev->next && prev->next->next){
            ListNode* first= prev->next;
            ListNode* second=prev->next->next;
            first->next=second->next;
            second->next=first;
            prev->next=second;
            prev=first;
        }
        return dummy->next;
    }
};
```
<img width="1919" height="852" alt="image" src="https://github.com/user-attachments/assets/5663ad37-49d3-4f9b-9609-070e9e06703f" />
