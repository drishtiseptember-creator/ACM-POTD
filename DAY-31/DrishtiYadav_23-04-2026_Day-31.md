```
int minCostClimbingStairs(int* cost, int costSize) {
    int prev2 = 0, prev1 = 0, curr;
    for(int i = 0; i < costSize; i++) {
        curr = cost[i] + (prev1 < prev2 ? prev1 : prev2);
        prev2 = prev1;
        prev1 = curr;
    }
    return prev1 < prev2 ? prev1 : prev2;
}
```