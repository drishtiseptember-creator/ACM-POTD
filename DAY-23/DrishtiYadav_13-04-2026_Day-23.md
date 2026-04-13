```
int findJudge(int n, int** trust, int trustSize, int* trustColSize) {
    int count[n + 1];
    for (int i = 1; i <= n; i++) {
        count[i] = 0;
    }
    for (int i = 0; i < trustSize; i++) {
        int a = trust[i][0];
        int b = trust[i][1];

        count[a]--;  
        count[b]++;  
    }
    for (int i = 1; i <= n; i++) {
        if (count[i] == n - 1) {
            return i;
        }
    }
    return -1;
}
```