```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
bool isPalindrome(struct ListNode* head) {
    struct ListNode* temp=head;
    int count=0, i;
    while(temp!=0){
        count++;
        temp=temp->next;
    }
    temp=head;
    struct ListNode* arr[count];
    for(i=0;i<count;i++){
        arr[i]=temp;
        temp=temp->next;

    }
    for(i=0;i<count/2;i++){
        if(arr[i]->val!=arr[count-1-i]->val){
            return false;
        }
    }
return true;
}
```