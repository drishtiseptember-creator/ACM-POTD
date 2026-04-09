```
bool backspaceCompare(char* s, char* t) {
    int i = strlen(s) - 1;
    int j = strlen(t) - 1;
    
    int skipS = 0, skipT = 0;

    while (i >= 0 || j >= 0) {
        
        // Process string s
        while (i >= 0) {
            if (s[i] == '#') {
                skipS++;
                i--;
            } else if (skipS > 0) {
                skipS--;
                i--;
            } else {
                break;
            }
        }
        
        // Process string t
        while (j >= 0) {
            if (t[j] == '#') {
                skipT++;
                j--;
            } else if (skipT > 0) {
                skipT--;
                j--;
            } else {
                break;
            }
        }
        
        // Compare characters
        if (i >= 0 && j >= 0) {
            if (s[i] != t[j]) return false;
        } else {
            if (i >= 0 || j >= 0) return false;
        }
        
        i--;
        j--;
    }
    
    return true;
}
```