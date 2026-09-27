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
    while (q.size() > 0) {
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
}

```
```
```

