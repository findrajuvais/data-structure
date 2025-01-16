# Graph Traversal (DFS, BFS):

Depth First Search (or DFS) for a graph, we traverse all adjacent vertices one by one. When we traverse an adjacent vertex, we completely finish the traversal of all vertices reachable through that adjacent vertex.

Breadth First Search (BFS) is a fundamental graph traversal algorithm. It begins with a node, then first traverses all its adjacent. Once all adjacent are visited, then their adjacent are traversed.


#### Graph traversal (BFS) Using Adjacency List:

```javascript
// First define make set for storing graph
function bfs(adj, src) {
  const visited = new Set();
  const queue = [];

  visited.add(src);
  queue.push(src);

  while (queue.length > 0) {
    const curr = queue.shift(); // get first element;
    console.log(curr);

    for (const x of adj[curr]) {
      if (!visited.has(x)) {
        visited.add(x);
        queue.push(x); // Enqueue unvisited neighbors
      }
    }
  }
}
```

#### DFS Traversal (Iterative version using a stack):

```javascript
function dfs(adj, src){
    const visited = new Set();
    const stack = [];
    stack.push(src);

    while (stack.length > 0) {
      const curr = stack.pop(); // Pop the last element

      if (!visited.has(curr)) {
        console.log(curr);
        visited.add(curr);
      }

      // Add all unvisited neighbors to the stack
      for (const x of adj[curr]) {
        if (!visited.has(x)) {
          stack.push(x);
        }
      }
    }
}
```


#### DFS Traversal (Recursive Approach):

```javascript
function dfsRecursive(adj, src, visited) {
    console.log(src);
    visited.add(src);

    // Visit all unvisited neighbors
    for (const x of adj[src]) {
      if (!visited.has(x)) {
        dfsRecursive(adj, x, visited);
      }
    }
  }
const visited = visited = new Set();
int x = 'A'
dfsRecursive(adj, x, visited);

```

#### Testcases:
```javascript
const adj = {
  A: ['B', 'C'],
  B: ['A', 'D', 'E'],
  C: ['A', 'F'],
  D: ['B'],
  E: ['B'],
  F: ['C']
};

console.log(dfs(adj, 'A')); // Output: [ 'A', 'B', 'D', 'E', 'C', 'F' ];
console.log(dfsRecursive(adj, 'A')); // Output: [ 'A', 'B', 'D', 'E', 'C', 'F' ];
console.log(bfs(graph, 'A'));  // Output: [ 'A', 'B', 'C', 'D', 'E', 'F' ]
```
