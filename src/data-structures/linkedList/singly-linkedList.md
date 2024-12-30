# LinkedList

A Linked List is a linear data structure where each element (or node) contains two parts:

1. Data: Stores the value or the content of the node.
2. Next: A reference (or pointer) to the next node in the sequence.

- Linked lists are dynamic in size, unlike arrays, and are often used when we need efficient insertion or deletion operations. Here’s a simple Singly Linked List implementation in JavaScript.

### Basic operations:

    1. append(data): Adds a node at the end of the list.
    2. prepend(data): Adds a node at the beginning of the list.
    3. delete(data): Deletes a node with the specified data.
    4. find(data): Finds a node with the specified data.
    5. display(): Displays all nodes in the list.

## Basic Implementation

### Types:(Singly Linked List, Doubly Linked List, Circular Linked List, Circular Doubly Linked List)

#### Singly Linked List:

A Singly Linked List is the simplest type of linked list. In this type, each node points to the next node in the sequence, and the last node points to null, indicating the end of the list.

##### Node class to represent each node in the linked list:

```javascript
class Node {
  constructor(data) {
    this.data = data; // Stores the data
    this.next = null; // Points to the next node
  }
}
```

##### Represent LinkedList:

```javascript
let head = null; // A reference to the first node.
let tail = null; // A reference to the last node.
let size = 0; // the number of the node lists.
```

##### Add a node to the end of the list:

```javascript
function append(data) {
  const newNode = new Node(data); // Create a new node with the data

  if (head === null) {
    head = newNode; // If the list is empty, new node is the head
    tail = newNode; // The new node is also the tail
  } else {
    tail.next = newNode; // Link the current tail to the new node
    tail = newNode; // Update the tail to the new node
  }
  size++; // Increase the size of the list
}
append(10);
append(20);
append(30);
```

##### Add a node to the beginning of the list:

```javascript
function prepend(data) {
  const newNode = new Node(data);
  if (head === null) {
    head = newNode;
    tail = newNode;
  } else {
    newNode.next = head; // Link new node to the current head
    head = newNode; // Update the head to the new node
  }
  size++; // Increase the size of the list
}
prepend(5); //output: 5 -> 10 -> 20 -> 30
prepend(1); //output: 1 -> 5 -> 10 -> 20 -> 30
```

##### Delete the first node with the specified data:

```javascript
function delete(data) {
    if (head === null) {
        return; // If the list is empty, nothing to delete
    }

    // If the head is the node to be deleted
    if (head.data === data) {
        head = head.next; // Update the head to the next node
        if (head === null) {
        tail = null; // If the list becomes empty, set tail to null
        }
        size--; // Decrease the size of the list
        return;
    }

    let current = head;
    while (current.next !== null) {
        if (current.next.data === data) {
        current.next = current.next.next; // Skip the node to be deleted
        if (current.next === null) {
            tail = current; // If the last node is deleted, update the tail
        }
        size--; // Decrease the size of the list
        return;
        }
        current = current.next; // Move to the next node
    }
}

delete(10); //output: 1 -> 5 -> 20 -> 30
delete(1); //output: 5 -> 20 -> 30
```

##### Find a node with the specified data:

```javascript
function find(data) {
  let current = head;
  while (current !== null) {
    if (current.data === data) {
      return current; // Return the node if found
    }
    current = current.next; // Move to the next node
  }
  return null; // Return null if the node is not found
}
find(20); // Output: Found Node: 20
find(40); // Output: Found Node: null
```

##### Display all nodes in the list:

```javascript
function display() {
  let current = head;
  let result = "";
  while (current !== null) {
    result += current.data + " -> ";
    current = current.next;
  }
  console.log(result ? result.slice(0, -4) : "Empty List"); // Remove last ' -> '
}
display(); // Output: 5 -> 20 -> 30
```

##### Get size of nodes in the list:

```javascript
function getSize() {
  return size;
}
getSize(); //Output: 3

/*** Time Complexity:
append(): O(1) - We keep a reference to the tail, so appending is fast.
prepend(): O(1) - Adding a node to the front is quick.
delete(): O(n) - In the worst case, we might have to traverse the entire list to find the node.
find(): O(n) - We need to traverse the list to find the node.
display(): O(n) - We need to go through the entire list to display its contents.
*/
```

## See Next:

- [Doubly Linked List](doubly-linkedList.md)
- [Circular Linked List](circular-linkedList.md)
- [Circular Doubly Linked List](circular-doubly-linkedList.md)
