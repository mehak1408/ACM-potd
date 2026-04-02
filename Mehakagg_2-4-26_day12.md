**This file contains all 3 questions of day 12**  
**Remove duplicates from list**
```
class Solution {
public:
    ListNode* deleteDuplicates(ListNode* head) {
        if(head==NULL)return NULL;
        ListNode* prev=head;
        ListNode* curr=head->next;
        while(curr!=NULL){
            if(prev->val==curr->val){
                prev->next=curr->next;
                curr=curr->next;
            }else{
                prev=curr;
                curr=curr->next;
            }
        }
        return head;
    }
};
```
<img width="1919" height="854" alt="image" src="https://github.com/user-attachments/assets/75adcbfe-ee7d-4ebe-900e-d385bbb14b28" />  

**Rotate list**
```
class Solution {
public:
    ListNode* rotateRight(ListNode* head, int k) {
        if(!head || !head->next || k==0){
            return head;
        }
        int len=0;
        ListNode* temp=head;
        while(temp!=NULL){
            len++;
            temp=temp->next;
        }
        k%=len;
        if(k==0)return head;
        while(k--){
            temp=head;
            while(temp->next->next!=NULL){
                temp=temp->next;
            }
            ListNode* newn= temp->next;
            temp->next=NULL;
            newn->next=head;
            head=newn;
        }
        return head;
    }
};
```
<img width="1918" height="858" alt="image" src="https://github.com/user-attachments/assets/7c941877-95c2-4106-a9a3-3edae42000c1" />  

**Copy list with random pointer**  
```
class Solution {
public:
    Node* copyRandomList(Node* head) {
        if(head==NULL)return head;
        unordered_map<Node*,Node*>m;
        Node* curr=head;
        while(curr){
            m[curr]=new Node(curr->val);
            curr=curr->next;
        }
        curr=head;
        while(curr){
            m[curr]->next=m[curr->next];
            m[curr]->random= m[curr->random];
            curr=curr->next;
        }
        return m[head];
    }
};
```
<img width="1918" height="906" alt="image" src="https://github.com/user-attachments/assets/d2312a1e-ff5e-45d4-9abc-3d7fc8dcb893" />
