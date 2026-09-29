# Topological Sort (Kahn's algorithm)

This is a particularly useful algorithm for things like scheduling / dependency, the overall idea is a take a graph and be able to convert this into an array of nodes in which each node has all of its dependencies (i.e. nodes that cause an in-degree) before it in the array. Now I know this sounds wacky but just bare with.

Steps to do this:
1. Make a hash-map that stores the in-degrees of each node
2. Push the nodes with 0 in-degree into the queue
3. Pop each node from the queue, subtract 1 from the in-degree of each of its dependents (neighbours)
4. If a neighbours' in-degree drops to 0, then push it into the queue
5. Repeat until the queue is empty. If any nodes remain unprocessed then there must be a cycle

## Generic Template

```cpp
template <typename T> 
std::unordered_map<T, int> find_indegree(std::unordered_map<T, std::vector<T>> graph) {
    std::unordered_map<T, int> indegree;
    for (auto entry : graph) {
        indegree[entry.first] = 0;
    }
    for (auto node : graph) {
        for (auto neighbor : node.second) {
            indegree[neighbor] += 1;
        }
    }
    return indegree;
}

template <typename T> 
std::vector<T> topo_sort(std::unordered_map<T, std::vector<T>> graph) {
    std::vector<T> res;
    std::queue<T> q;
    std::unordered_map<T, int> indegree = find_indegree(graph);
    for (auto entry : indegree) {
        if (entry.second == 0) q.push(entry.first);
    }
    while (q.size() > 0) {
        T node = q.front();
        res.emplace_back(node);
        for (T neighbor : graph[node]) {
            indegree[neighbor] -= 1;
            if (indegree[neighbor] == 0) q.push(neighbor);
        }
        q.pop();
    }
    if (graph.size() == res.size()) return res;
    else {
        std::cout << "Invalid topo sort: graph contains cycle" <<'\n';
        return std::vector<T>();
    }
}
```

