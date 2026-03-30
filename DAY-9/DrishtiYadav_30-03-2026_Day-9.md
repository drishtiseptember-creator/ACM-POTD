```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
bool hasCycle(struct ListNode *head) {
      struct ListNode* onestep,*twostep;
      onestep=twostep=head;
      while(twostep!=NULL && twostep->next!=NULL){
        onestep=onestep->next;
        twostep=twostep->next->next;
        if(onestep==twostep){
            return true;
        }
      }
      return false;
}
```