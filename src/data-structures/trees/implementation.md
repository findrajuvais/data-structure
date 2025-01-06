# TREE

A tree is a hierarchical data structure that consists of nodes, where each node contains a value and references to its child nodes. In JavaScript, you can implement a tree using classes or objects.

##### Define tree node:

```javascript
class Node {
  constructor(data) {
    this.data = data;        // Data for this node
    this.children = [];      // Array to hold child nodes
  }
}
```

##### Implemenation of general tree:

```javascript

class Tree{
    this.root = null;
}
```
##### Search data under specific parent node:

```javascript
Tree.prototype.search = function(data){
    return this.searchNode(this.root, data)
}
```

##### Helper method for search node under specific parent node:
```javascript
Tree.prototype.searchNode = function(node, data){
    if(node == null) return null;

    if(node.data == data) return node;

    for(let child of node.children){
        const foundNode = this.searchNode(child, data);
        if(foundNode) return foundNode;
    }
    return null;
}
```

##### Insert a node under specific parent node:

```javascript
Tree.prototype.insert = function(parentData, data){
    const newNode = new Node(data);
    
    if (this.root === null) {
      // If the tree is empty, the first node is the root
      this.root = newNode;
    } else {
      const parentNode = this.search(parentData);
      if (parentNode) {
        parentNode.children.push(newNode);  // Add as a child of the parent
      } else {
        console.log('Parent node not found');
      }
    }
}
```

##### Preorder traversal:
```javascript
Tree.prototype.preOrder = function(){
    return this.preOrderTraversal(this.root);
}
```

##### Helper method for preOrder traversal of trees:
```javascript
Tree.prototype.preOrderTraversal = function(parentNode){
    if(parentNode == null) return null;
    console.log(parentNode.data);

    for(child of parentNode.children){
        this.preOrderTraversal(child);
    }
}
```


##### postOrder traversal:
```javascript
Tree.prototype.postOrder = function(){
    return this.postOrderTraversal(this.root);
}
```

##### Helper method for postOrder traversal of trees:
```javascript
Tree.prototype.postOrderTraversal = function(parentNode){
    if(parentNode == null) return null;
    
    for(child of parentNode.children){
        this.postOrderTraversal(child);
    }

    console.log(parentNode.data);
}
```

##### Find hight of tree:
```javascript

Tree.prototype.height = function(){
    return this.treeHeight(this.root);
}
```

##### Helper method to get height of tree:

```javascript

Tree.prototype.heightOfTree = function(node){
    if(node == null) return 0;

    if(node.children.length === 0) return 1;

    let maxChildHeight= 0;

    for(const child of node.children){
        const childHeight = this.heightOfTree(child);
        maxChildHeight = Math.max(maxChildHeight, childHeight);
    }

    return maxChildHeight + 1;
}
```

##### Delete a node with a specific value:

```javascript
Tree.prototype.delete = function(data){
    return this.deleteNode(this.root, data);
}

```

##### Helper method for Delete a node with a specific value:

```javascript
Tree.prototype.deleteNode = function(node, data){
    if(node === null) return null;

    if(node.data === data) return null;

    node.children = node.children.map(child => {
        this.deleteNode(child, data).filter(child => child !== null);
    })
    return node;
}

```

##### Print the tree (to visualize structure):
```javascript
Tree.prototype.printTree = function() {
    this.printTreeHelper(this.root, 0);
}
```

##### Helper method for printing tree in a readable format
```javascript
Tree.prototype.printTreeHelper = function(node, level) {
    if (node === null) return;
    console.log(' '.repeat(level * 2) + node.data);
    for (let child of node.children) {
        this.printTreeHelper(child, level + 1);
    }
}
```

##### Tests:
```javascript
// Create a tree
const tree = new Tree();

// Insert nodes into the tree
tree.insert(null, 'Root');  // Root is the first node
tree.insert('Root', 'Child1');
tree.insert('Root', 'Child2');
tree.insert('Child1', 'Child1-1');
tree.insert('Child1', 'Child1-2');
tree.insert('Child2', 'Child2-1');

// Print the tree structure
console.log('Tree structure:');
tree.printTree();
// Output:
// Root
//   Child1
//     Child1-1
//     Child1-2
//   Child2
//     Child2-1

// Perform pre-order traversal
console.log('Pre-order Traversal:');
tree.preOrder(); // Output: Root, Child1, Child1-1, Child1-2, Child2, Child2-1

// Perform post-order traversal
console.log('Post-order Traversal:');
tree.postOrder(); // Output: Child1-1, Child1-2, Child1, Child2-1, Child2, Root

// Find the height of the tree
console.log('Height of the tree:', tree.height()); // Output: 3

// Delete a node
tree.delete('Child1-1');
console.log('Tree structure after deletion:');
tree.printTree();
// Output:
// Root
//   Child1
//     Child1-2
//   Child2
//     Child2-1

```


### Next:
- [Binary Tree](binary-tree.md)
- [Binary Search Tree](binary-search-tree.md)
