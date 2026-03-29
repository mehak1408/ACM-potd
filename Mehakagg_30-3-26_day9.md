**Linked list cycle**
```
class public:
    bool hasCycle(ListNode *head) {
        ListNode* slow= head;
        ListNode* fast= head;
        while(fast!=NULL && fast->next!=NULL){
            fast=fast->next->next;
            slow=slow->next;
            if(slow==fast){
                return true;
            }
        }
        return false;
    }
};
```
![118617](https://github.com/user-attachments/assets/473562d2-cdbb-4025-a477-6e8e1ce5ff94)
