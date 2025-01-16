# Graph

A Graph is a non-linear data structure consisting of vertices and edges. The vertices are sometimes also referred to as nodes and the edges are lines or arcs that connect any two nodes in the graph.

V - vertices
E - Edges

Denoted by G(V, E)

### Representation of Graph:

Two most common way to represent graph:

1. Adjacency Matrix
2. Adjacency list

#### Adjacency Matrix Representation undirected:

```javascript
/**
 *(1)---(2)
 * \     /
 *  \   /
 *   \ /
 *   (0)
 *
 *
 * undirected graph
 * G(0,1)
 * G(1,0)
 * G(0,2)
 * G(2,0)
 * G(1,2)
 * G(2,1)
 *
 *
 */
function addEdge(mat, i, j) {
  mat[i][j] = 1; // Graph is undirected
  mat[j][i] = 1;
}

function displayMatrix(mat) {
  // Display the adjacency matrix
  for (const row of mat) {
    console.log(row.join(" "));
  }
}

const V = 3;
let mat = Array.from({ length: V }, () => Array(V).fill(0));

// Add edges to the graph
addEdge(mat, 0, 1);
addEdge(mat, 0, 2);
addEdge(mat, 1, 2);
addEdge(mat, 2, 3);

console.log("Adjacency Matrix:");
displayMatrix(mat);

/**
 * ## Adjacency Matrix Representation Output:
 * 0 1 1
 * 1 0 1
 * 1 1 0
 */
```

#### Adjacency List Representation For undirected graph:

```javascript
function addEdge(adj, i, j) {
  adj[i].push(j); // Graph is undirected
  adj[j].push(i);
}

function displayList(adj) {
  // Display the adjacency list
  for (let i = 0; i < adj.length; i++) {
    let line = i + ": ";
    for (let j of adj[i]) {
      line += j + " ";
    }
    console.log(line);
  }
}

let V = 3;
let adj = Array.from({ length: V }, () => []);

// Add edges to the graph
addEdge(adj, 0, 1);
addEdge(adj, 0, 2);
addEdge(adj, 1, 2);

console.log("Adjacency List Representation:");
displayList(adj);

/**
 *Adjacency List Representation:
 * 0: 1 2
 * 1: 0 2
 * 2: 1 0
 */
```

#### Adjacency list and matrix representation for directed graph:

```javascript
/***
 * vertex: 0->1->2->0
 *
 * means represent with matrix only like below
 */

function addEdge(mat, i, j) {
  mat[i][j] = 1;
}

/***
 * vertex: 0->1->2->0
 *
 * means represent with List only like below
 */

function addEdge(mat, i, j) {
  mat[i].push(j);
}
```

#### Adjacency list and matrix representation with weighted for directed and undirected:

```javascript
//Matrix for direct and undirect with weight
//1. undirected graph
function addEdge(mat, i, j, w) {
    mat[i][j] = w;
    mat[j][i] = w;
}

//2. directed graph
function addEdge(mat, i, j, w) {
    mat[i][j] = w;
}

//List for direct and undirect with weight
//1. undirected graph
function addEdge(mat, i, j, w) {
    mat[i].push([j,w]);
    mat[j].push([i,w]);
}

//2. directed graph
function addEdge(mat, i, j, w) {
    mat[i].push([j,w]);
}
```
#### Next:
- [Traversal (DFS, BFS)](graph-traversal.md)


