# BFS on a graph

So you just do BFS starting at a node N for all the neighbours, pretty simple stuff also feels / looks really cool.

## Generic template

```cpp
#include <queue>
#include <unordered_set>

void bfs(Node<int>* root) {
    std::queue<Node<int>*> q;
    q.push(root);
    std::unordered_set<Node<int>*> visited{root};
    // level to track how many layers we've gone through (i.e. sets of neighbours)
    int level{};
    while (q.size() > 0) {
      int s = q.size();
      for (int i = 0; i < s; i++) {
        Node<int>* node = q.front();
        for (Node<int>* neighbor : get_neighbors(node)) {
            if (visited.count(neighbor)) {
                continue;
            }
            q.push(neighbor);
            visited.insert(neighbor);
        }
        q.pop();
     }
    level++;
    }
}

```
```
```

