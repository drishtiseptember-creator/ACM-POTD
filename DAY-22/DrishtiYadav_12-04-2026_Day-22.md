```
void dfs(int** image, int rows, int cols, int r, int c, int oldColor, int newColor) {
    if (r < 0 || c < 0 || r >= rows || c >= cols)
        return;
    if (image[r][c] != oldColor)
        return;
    image[r][c] = newColor;
    dfs(image, rows, cols, r + 1, c, oldColor, newColor);
    dfs(image, rows, cols, r - 1, c, oldColor, newColor);
    dfs(image, rows, cols, r, c + 1, oldColor, newColor);
    dfs(image, rows, cols, r, c - 1, oldColor, newColor);
}
int** floodFill(int** image, int imageSize, int* imageColSize, int sr, int sc, int color, int* returnSize, int** returnColumnSizes) {
    *returnSize = imageSize;
    *returnColumnSizes = imageColSize;
    int oldColor = image[sr][sc];
        if (oldColor == color)
        return image;
    dfs(image, imageSize, imageColSize[0], sr, sc, oldColor, color);
    return image;
}
```