# Binary Search Tree:

A Binary Search Tree (BST) is a type of binary tree where each node follows these specific rules:

1. Left Subtree: The left subtree of a node contains only nodes with values less than the node's value.
2. Right Subtree: The right subtree of a node contains only nodes with values greater than the node's value.
3. No Duplicates: Typically, a BST does not allow duplicate values, though variations can support duplicates.

### Properties of a Binary Search Tree:

Searching: Binary Search Trees support efficient searching, as they take advantage of the binary search principle. For a node, you can compare it with the root:
If the target is smaller, search the left subtree.
If the target is larger, search the right subtree.

Insertion/Deletion: Insertion and deletion operations are also efficient, typically having an average time complexity of O(log n) if the tree is balanced.

Traversal: There are several ways to traverse a BST:
In-order traversal: Visits nodes in ascending order (left, root, right).
Pre-order traversal: Visits nodes in the order (root, left, right).
Post-order traversal: Visits nodes in the order (left, right, root).

##### Create binary search tree node:

```javascript
class Node {
  constructor(data) {
    this.data = data;
    this.left = null;
    this.right = null;
  }
}
```

##### DFS traversal algorithms using Recursive approach:

```javascript
// In-Order Traversal: Left, Root, Right
function inOrder(root) {
  if (root !== null) {
    inorder(root.left);
    console.log(root.key + " ");
    inorder(root.right);
  }
}

// Pre-Order Traversal: Root, Left, Right
function preOrder(root) {
  if (root !== null) {
    console.log(root.key + " ");
    inorder(root.left);
    inorder(root.right);
  }
}

// Post-Order Traversal: Left, Right, Root
function postOrder(root) {
  if (root !== null) {
    inorder(root.left);
    inorder(root.right);
    console.log(root.key + " ");
  }
}
```

##### Insertion in Binary Search Tree Using Recursive approach:

```javascript
// node with the given key
function insert(root, key) {
  if (root === null) return new Node(key);

  // Duplicates not allowed
  if (root.key === key) return root;

  if (key < root.key) root.left = insert(root.left, key);
  else if (key > root.key) root.right = insert(root.right, key);

  return root;
}

// Creating the following BST
//      50
//     /  \
//    30   70
//   / \   / \
//  20 40 60 80

let root = new Node(50);
root = insert(root, 30);
root = insert(root, 20);
root = insert(root, 40);
root = insert(root, 70);
root = insert(root, 60);
root = insert(root, 80);

// Print inorder traversal of the BST
inOrder(root);
```

##### Insert in binary search tree using iterative approach:

```javascript
function insert(root, x) {
  const temp = new Node(x);

  // If tree is empty
  if (root === null) return temp;

  // Find the node who is going to have
  // the new node temp as its child
  let parent = null;
  let curr = root;
  while (curr !== null) {
    parent = curr;
    if (curr.key > x) curr = curr.left;
    else if (curr.key < x) curr = curr.right;
    else return root; // Key already exists
  }

  // If x is smaller, make it left
  // child, else right child
  if (parent.key > x) parent.left = temp;
  else parent.right = temp;

  return root;
}
```

##### Implement search in binary search tree using recursive approach:
```javascript
function search(root, key)
{

    // Base Cases: root is null or key is 
    // present at root
    if (root === null || root.key === key)
        return root;

    // Key is greater than root's key
    if (root.key < key)
        return search(root.right, key);

    // Key is smaller than root's key
    return search(root.left, key);
}
```

##### Implement search in binary search tree using iterative approach:
```javascript
function search(root, x) {
    
    let curr = root;
    
    while (curr !== null) {
        
        // If curr node is x
        if (curr.data === x)
            return true;
            
        // Search in right subtree
        else if (curr.data < x) 
            curr = curr.right;
            
        // Search in left subtree
        else
            curr = curr.left;
    }
    
    // If x is not found.
    return false;
}
```

##### Delete in BST using Recursive Approach:

```javascript
// Note that it is not a generic inorder successor
// function. It mainly works when the right child 
// is not empty, which is  the case we need in BST
// delete.
function getSuccessor(curr) {
    curr = curr.right;
    while (curr !== null && curr.left !== null) {
        curr = curr.left;
    }
    return curr;
}

// This function deletes a given key x from the
// given BST and returns the modified root of the
// BST (if it is modified).
function delNode(root, x) {
    // Base case
    if (root === null) {
        return root;
    }

    // If key to be searched is in a subtree
    if (root.key > x) {
        root.left = delNode(root.left, x);
    } else if (root.key < x) {
        root.right = delNode(root.right, x);
    } else {
        // If root matches with the given key

        // Cases when root has 0 children or 
        // only right child
        if (root.left === null) 
            return root.right;

        // When root has only left child
        if (root.right === null) 
            return root.left;

        // When both children are present
        let succ = getSuccessor(root);
        root.key = succ.key;
        root.right = delNode(root.right, succ.key);
    }
    return root;
}
```

##### Delete in BST using Iterative Approach:
```javascript
function delIterative(root, key) {
    let curr = root;
    let prev = null;

    // Check if the key is actually present in the BST.
    // The variable prev points to the parent of the key
    // to be deleted.
    while (curr !== null && curr.key !== key) {
        prev = curr;
        if (key < curr.key) {
            curr = curr.left;
        } else {
            curr = curr.right;
        }
    }

    // Key not present
    if (curr === null) {
        return root;
    }

    // Check if the node to be deleted has at most one child.
    if (curr.left === null || curr.right === null) {
        let newCurr = (curr.left === null) ? curr.right : curr.left;

        // Check if the node to be deleted is the root.
        if (prev === null) {
            return newCurr;
        }

        // Check if the node to be deleted is prev's left or
        // right child and then replace this with newCurr.
        if (curr === prev.left) {
            prev.left = newCurr;
        } else {
            prev.right = newCurr;
        }
        
    } else {
        // Node to be deleted has two children.
        let p = null;
        let temp = curr.right;
        while (temp.left !== null) {
            p = temp;
            temp = temp.left;
        }

        if (p !== null) {
            p.left = temp.right;
        } else {
            curr.right = temp.right;
        }

        curr.key = temp.key;
    }

    return root;
}

```

### Next:

- [Tree Implementation](implementation.md)
- [Binary Tree](binary-tree.md)
