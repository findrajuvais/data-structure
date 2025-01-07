# Binary Tree

A Binary Tree Data Structure is a hierarchical data structure in which each node has at most two children, referred to as the left child and the right child. It is commonly used in computer science for efficient storage and retrieval of data, with various operations such as insertion, deletion, and traversal.

### Representation of binary tree:

1. data
2. pointer to the left tree
3. pointer to the right tree

##### Create/Declare a Node of a Binary Tree:

```javascript
class Node(){
    constructor(data){
        this.data = data;
        this.left = null;
        this.right = null;
    }
}
```

##### Creating a binary tree:

```javascript
// Initialize and allocate memory for tree nodes
let firstNode = new Node(10);
let secondNode = new Node(20);
let thirdNode = new Node(30);
let fourthNode = new Node(40);
let fifthNode = new Node(50);

// Connect binary tree nodes
firstNode.left = secondNode;
firstNode.right = thirdNode;
secondNode.left = fourthNode;
secondNode.right = fifthNode;
```

### Terminologies in Binary Tree:

- Nodes: The fundamental part of a binary tree, where each node contains data and link to two child nodes.
- Root: The topmost node in a tree is known as the root node. It has no parent and serves as the starting point for all nodes in the tree.
- Parent Node: A node that has one or more child nodes. In a binary tree, each node can have at most two children.
- Child Node: A node that is a descendant of another node (its parent).
- Leaf Node: A node that does not have any children or both children are null.
- Internal Node: A node that has at least one child. This includes all nodes except the root and the leaf nodes.
- Depth of a Node: The number of edges from a specific node to the root node. The depth of the root node is zero.
- Height of a Binary Tree: The number of nodes from the deepest leaf node to the root node.

### Properties of Binary Tree:

- The maximum number of nodes at level L of a binary tree is 2L
- The maximum number of nodes in a binary tree of height H is 2H – 1
- Total number of leaf nodes in a binary tree = total number of nodes with 2 children + 1
- In a Binary Tree with N nodes, the minimum possible height or the minimum number of levels is Log2(N+1)
- A Binary Tree with L leaves has at least | Log2L |+ 1 levels

### Type of Binary Tree:

1. On the basis of Number of Children

   - Full Binary Tree
   - Degenerate Binary Tree
   - Skewed Binary Trees

2. On the basis of Completion of Levels

   - Complete Binary Tree
   - Perfect Binary Tree
   - Balanced Binary Tree

3. On the basis of Node Values
   - Binary Search Tree
   - AVL Tree
   - Red Black Tree
   - B Tree
   - B+ Tree
   - Segment Tree

#### Traversal in Binary Tree:

Tree traversal classified into two categories: DFS, BFS

DFS (Depth-First-Search):

1. Preorder Traversal (current-left-right): Visits the node first, then left subtree, then right subtree.
2. Inorder Traversal (left-current-right): Visits left subtree, then the node, then the right subtree.
3. Postorder Traversal (left-right-current): Visits left subtree, then right subtree, then the node.

BFS (Breadth-First-Search):
Leval Order Traversal.

##### Implementation of traversal algorithm binary tree:

```javascript
// In-order DFS: Left, Root, Right
function inOrderDFS(node) {
  if (node === null) return;
  inOrderDFS(node.left);
  console.log(node.data + " ");
  inOrderDFS(node.right);
}

// Pre-order DFS: Root, Left, Right
function preOrderDFS(node) {
  if (node === null) return;
  console.log(node.data + " ");
  preOrderDFS(node.left);
  preOrderDFS(node.right);
}

// Post-order DFS: Left, Right, Root
function postOrderDFS(node) {
  if (node === null) return;
  postOrderDFS(node.left);
  postOrderDFS(node.right);
  console.log(node.data + " ");
}

// BFS: Level order traversal
function bfs(root) {
  if (root === null) return;
  let queue = [root];
  while (queue.length > 0) {
    let node = queue.shift();
    console.log(node.data + " ");
    if (node.left) queue.push(node.left);
    if (node.right) queue.push(node.right);
  }
}
```

##### Insertion of Binary Tree:

```javascript
function insert(root, key) {
  if (root === null) {
    return new Node(key);
  }

  // Create a queue for level order traversal
  let queue = [root];

  while (queue.length > 0) {
    let temp = queue.shift();

    // If left child is empty, insert the new node here
    if (temp.left === null) {
      temp.left = new Node(key);
      break;
    } else {
      queue.push(temp.left);
    }

    // If right child is empty, insert the new node here
    if (temp.right === null) {
      temp.right = new Node(key);
      break;
    } else {
      queue.push(temp.right);
    }
  }

  return root;
}
```

##### Search in Binary Tree:

```javascript
function searchDFS(root, value) {
  // Base case: If the tree is empty or we've reached a leaf node
  if (root === null) {
    return false;
  }
  // If the node's data is equal to the value we are searching for
  if (root.data === value) {
    return true;
  }
  // Recursively search in the left and right subtrees
  const left_res = searchDFS(root.left, value);
  const right_res = searchDFS(root.right, value);

  return left_res || right_res;
}
```

##### Deletion in Binary Tree:

```javascript
function deleteNode(root, val) {
  if (root === null) return null;

  // Use a queue to perform BFS
  let queue = [root];
  let target = null;

  // Find the target node
  while (queue.length > 0) {
    let curr = queue.shift();

    if (curr.data === val) {
      target = curr;
      break;
    }
    if (curr.left) queue.push(curr.left);
    if (curr.right) queue.push(curr.right);
  }
  if (target === null) return root;

  // Find the deepest rightmost node and its parent
  let lastNode = null;
  let lastParent = null;
  queue = [{ node: root, parent: null }];

  while (queue.length > 0) {
    let { node: curr, parent } = queue.shift();
    lastNode = curr;
    lastParent = parent;

    if (curr.left) queue.push({ node: curr.left, parent: curr });
    if (curr.right) queue.push({ node: curr.right, parent: curr });
  }

  // Replace target's value with the last node's value
  target.data = lastNode.data;

  // Remove the last node
  if (lastParent) {
    if (lastParent.left === lastNode) lastParent.left = null;
    else lastParent.right = null;
  } else {
    return null;
  }
  return root;
}
```

### Next:

- [Binary Search Tree](binary-search-tree.md)
- [Tree Implementation](implementation.md)
