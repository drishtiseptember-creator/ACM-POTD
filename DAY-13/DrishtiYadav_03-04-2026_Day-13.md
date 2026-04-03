```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode *getIntersectionNode(struct ListNode *headA, struct ListNode *headB) {
    if (!headA || !headB) return NULL;

    int lenA = 0, lenB = 0;
    struct ListNode *tA = headA, *tB = headB;

    while (tA) { lenA++; tA = tA->next; }
    while (tB) { lenB++; tB = tB->next; }

    while (lenA > lenB) {
        headA = headA->next;
        lenA--;
    }
    while (lenB > lenA) {
        headB = headB->next;
        lenB--;
    }

    struct ListNode *tempA1 = NULL, *tempA2 = headA, *tempA3 = NULL;
    struct ListNode *tempB1 = NULL, *tempB2 = headB, *tempB3 = NULL;

    while (tempA2 != NULL && tempB2 != NULL) {

        tempA3 = tempA2->next;
        tempB3 = tempB2->next;

        if (tempA2 == tempB2) return tempA2;
        if (tempA1 && tempB1 && tempA1 == tempB1) return tempA1;
        if (tempA3 && tempB3 && tempA3 == tempB3) return tempA3;

        tempA1 = tempA2;
        tempA2 = tempA2->next;

        tempB1 = tempB2;
        tempB2 = tempB2->next;
    }

    return NULL;
}
```