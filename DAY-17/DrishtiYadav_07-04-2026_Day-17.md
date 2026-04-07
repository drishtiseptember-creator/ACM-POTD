```
#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>

#define SIZE 1000

typedef struct {
    int *q1;
    int *q2;
    int front1, rear1;
    int front2, rear2;
} MyStack;

// Queue helpers
void enqueue(int q[], int *front, int *rear, int x) {
    if (*rear == SIZE - 1) return;
    if (*front == -1) *front = 0;
    q[++(*rear)] = x;
}

int dequeue(int q[], int *front, int *rear) {
    if (*front == -1) return -1;
    int val = q[*front];
    if (*front == *rear)
        *front = *rear = -1;
    else
        (*front)++;
    return val;
}

bool isEmpty(int front) {
    return front == -1;
}

/** Initialize your data structure here. */
MyStack* myStackCreate() {
    MyStack* obj = (MyStack*)malloc(sizeof(MyStack));

    obj->q1 = (int*)malloc(SIZE * sizeof(int));
    obj->q2 = (int*)malloc(SIZE * sizeof(int));

    obj->front1 = obj->rear1 = -1;
    obj->front2 = obj->rear2 = -1;

    return obj;
}

/** Push element x onto stack. */
void myStackPush(MyStack* obj, int x) {
    // Step 1: push into q2
    enqueue(obj->q2, &obj->front2, &obj->rear2, x);

    // Step 2: move all elements from q1 → q2
    while (!isEmpty(obj->front1)) {
        enqueue(obj->q2, &obj->front2, &obj->rear2,
                dequeue(obj->q1, &obj->front1, &obj->rear1));
    }

    // Step 3: swap q1 and q2
    int *tempQ = obj->q1;
    obj->q1 = obj->q2;
    obj->q2 = tempQ;

    int tempF = obj->front1;
    obj->front1 = obj->front2;
    obj->front2 = tempF;

    int tempR = obj->rear1;
    obj->rear1 = obj->rear2;
    obj->rear2 = tempR;
}

/** Removes the element on top of the stack and returns it. */
int myStackPop(MyStack* obj) {
    return dequeue(obj->q1, &obj->front1, &obj->rear1);
}

/** Get the top element. */
int myStackTop(MyStack* obj) {
    if (obj->front1 == -1) return -1;
    return obj->q1[obj->front1];
}

/** Returns whether the stack is empty. */
bool myStackEmpty(MyStack* obj) {
    return isEmpty(obj->front1);
}

void myStackFree(MyStack* obj) {
    free(obj->q1);
    free(obj->q2);
    free(obj);
}
```