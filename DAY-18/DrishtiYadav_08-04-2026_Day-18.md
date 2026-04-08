```
char* removeDuplicates(char* s) {
    int i = 0, top = -1;
    
    while (s[i] != '\0') {
        if (top >= 0 && s[top] == s[i]) {
            // duplicate → remove
            top--;
        } else {
            // push current character
            s[++top] = s[i];
        }
        i++;
    }
    
    s[top + 1] = '\0';  // terminate string
    return s;
}
```