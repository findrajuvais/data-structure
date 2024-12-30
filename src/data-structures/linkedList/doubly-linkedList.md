# LinkedList (Doubly Linked List):

A Doubly Linked List allows traversal in both directions (forward and backward). Each node contains three parts:

    1. Data: Stores the value of the node.
    2. Next: A reference to the next node.
    3. Prev: A reference to the previous node.

##### Node class to represent each node in the linked list:

```javascript
class Node {
  constructor(data) {
    this.data = data; // Stores the data
    this.next = null; // Points to the next node
    this.prev = null; // Points to the next node
  }
}
```

##### Represent LinkedList:

```javascript
let head = null; // A reference to the first node.
let tail = null; // A reference to the last node.
let size = 0; // the number of the node lists.
```

##### Insert at the head of the list:

```javascript
function insertAtHead(data) {
  const newNode = new Node(data);
  if (!head) {
    head = tail = newNode; // If the list is empty
  } else {
    newNode.next = head;
    head.prev = newNode;
    head = newNode;
  }
}
```

##### Insert at the tail of the list:

```javascript
function insertAtTail(data) {
  const newNode = new Node(data);
  if (!tail) {
    head = tail = newNode; // If the list is empty
  } else {
    tail.next = newNode;
    newNode.prev = tail;
    tail = newNode;
  }
}
```

##### Insert at a specific index:

```javascript
function insertAtIndex(index, data) {
  if (index < 0) return; // Invalid index
  if (index === 0) return insertAtHead(data);

  let newNode = new Node(data);
  let current = head;
  let count = 0;

  // Traverse the list to find the index
  while (current && count < index) {
    current = current.next;
    count++;
  }

  if (!current) return; // Index out of bounds
  newNode.next = current;
  newNode.prev = current.prev;
  current.prev.next = newNode;
  current.prev = newNode;
}
```

##### Remove a node from the head:

```javascript
function emoveFromHead() {
  if (!head) return; // If the list is empty

  if (head === tail) {
    head = tail = null; // List becomes empty
  } else {
    head = head.next;
    head.prev = null;
  }
}
```

##### Remove a node from the tail:

```javascript
function removeFromTail() {
  if (!tail) return; // If the list is empty

  if (head === tail) {
    head = tail = null; // List becomes empty
  } else {
    tail = tail.prev;
    tail.next = null;
  }
}
```

##### Remove a node at a specific index:

```javascript
function removeAtIndex(index) {
  if (index < 0) return; // Invalid index
  if (index === 0) return removeFromHead();

  let current = head;
  let count = 0;

  // Traverse the list to find the node at the given index
  while (current && count < index) {
    current = current.next;
    count++;
  }

  if (!current) return; // Index out of bounds
  // Re-link the previous and next nodes to remove the current node
  if (current.prev) current.prev.next = current.next;
  if (current.next) current.next.prev = current.prev;
}
```

##### Print the list from head to tail:

```javascript
function printForward() {
  let current = head;
  let result = [];
  while (current) {
    result.push(current.data);
    current = current.next;
  }
  console.log(result.join(" <-> "));
}
```

##### Print the list from tail to head:

```javascript
function printBackward() {
  let current = tail;
  let result = [];
  while (current) {
    result.push(current.data);
    current = current.prev;
  }
  console.log(result.join(" <-> "));
}
```

##### Tests:

```javascript
// Insert at the head
insertAtHead(10);
insertAtHead(20);
insertAtHead(30);

// Insert at the tail
insertAtTail(5);
insertAtTail(1);

// Insert at a specific index (index 2)
insertAtIndex(2, 15);

console.log("Forward traversal:");
printForward(); // Output: 30 <-> 20 <-> 15 <-> 10 <-> 5 <-> 1

console.log("Backward traversal:");
printBackward(); // Output: 1 <-> 5 <-> 10 <-> 15 <-> 20 <-> 30

// Remove from the head
removeFromHead();
console.log("\nAfter removing from head:");
printForward(); // Output: 20 <-> 15 <-> 10 <-> 5 <-> 1

// Remove from the tail
removeFromTail();
console.log("\nAfter removing from tail:");
printForward(); // Output: 20 <-> 15 <-> 10 <-> 5

// Remove at a specific index (index 1)
removeAtIndex(1);
console.log("\nAfter removing at index 1:");
printForward(); // Output: 20 <-> 10 <-> 5
```

## See Next:

- [Circular Linked List](circular-linkedList.md)
- [Circular Doubly Linked List](circular-doubly-linkedList.md)
- [Singly Linked List](singly-linkedList.md)
