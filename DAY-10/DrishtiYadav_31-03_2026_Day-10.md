```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode* middleNode(struct ListNode* head) {
    struct ListNode *temp = head;
    int count = 0;
    int mid;
    while(temp != NULL){
        count++;
        temp = temp->next;
    }
    temp = head;
    if( count%2==0){
        mid=(count/2)+1;
    }
    else{
        mid=(count+1)/2;
    }
    for( int i= 0; i < mid-1; i++){
        temp=temp->next;
    }
    return temp;
}
```