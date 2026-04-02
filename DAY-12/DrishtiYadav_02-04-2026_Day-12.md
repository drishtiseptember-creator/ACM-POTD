```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode* deleteDuplicates(struct ListNode* head) {
    struct ListNode* constant,*move,*temp;
    constant=move=temp=head;
    if (head == NULL) {
    return head;
    }
    while(constant!=NULL && constant->next!=NULL){
        move=temp=constant;
        while(move!=NULL && move->next!=NULL){
            temp=move;
            move=move->next;
            if(constant->val==move->val){
                temp->next=move->next;
                move=temp;
            }
        }

        constant=constant->next;
    }
return head;
}
```