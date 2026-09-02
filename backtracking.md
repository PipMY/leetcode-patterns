# Backtracking

Build a decision tree one step at a time. When the choice doesn't work, undo it and try another. Therefore trying every possible solution. And you collect the answers you want when they fit some criteria that you set ie the string is of length 4.

## Generic Template

```cpp
void dfs(State& state) {
    if (isSolution(state)) {
        results.push_back(state);
        return;
    }

    for (auto choice : choices(state)) {
        makeChoice(state, choice);

        dfs(state);

        undoChoice(state, choice);
    }
}
```
