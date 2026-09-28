# Floodfill

So this is the floodfill algorithm for graphs very useful to have for some questions tbh.

# Generic Template

```cpp
std::vector<std::vector<int>> flood_fill(
    int r, int c, int replacement, std::vector<std::vector<int>>& image
) {
    int rows = image.size();
    int cols = image[0].size();
    int original = image[r][c];

    if (original == replacement) {
        return image;
    }

    std::queue<std::pair<int, int>> q;
    q.push({r, c});
    image[r][c] = replacement;

    while (!q.empty()) {
        auto [row, col] = q.front();
        q.pop();

        const int dr[] = {-1, 1, 0, 0};
        const int dc[] = {0, 0, -1, 1};

        for (int i = 0; i < 4; ++i) {
            int next_row = row + dr[i];
            int next_col = col + dc[i];

            if (next_row >= 0 && next_row < rows &&
                next_col >= 0 && next_col < cols &&
                image[next_row][next_col] == original) {
                image[next_row][next_col] = replacement;
                q.push({next_row, next_col});
            }
        }
    }

    return image;
}
```
```
```
