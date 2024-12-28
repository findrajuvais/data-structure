# LinkedList (Circular Doubly Linked List):

    A Circular Doubly Linked List (CDLL) is a variation of a Doubly Linked List where the first node's previous pointer points to the last node, and the last node's next pointer points to the first node, forming a circular structure. Each node in this list has two pointers:
        next: Points to the next node in the list.
        prev: Points to the previous node in the list.

    In a Circular Doubly Linked List:
        Head's previous points to the last node.
        Tail's next points to the head.

#### Key Features:

1. Circular: Both the head.prev points to the tail, and tail.next points to the head.
2. Doubly Linked: Each node contains pointers to both the next and previous nodes.

##### Node class to represent each node in the linked list:

```javascript
class Node {
  constructor(data) {
    this.data = data; // The value of the node
    this.next = null; // Pointer to the next node
    this.prev = null; // Pointer to the previous node
  }
}
```

##### Represent LinkedList:

```javascript
let head = null; // A reference to the first node.
let tail = null; // A reference to the last node.
let size = 0; // the number of the node lists.
```

##### Insert at the end of the circular doubly linked list

```javascript
function insertAtEnd(data) {
  const newNode = new Node(data);

  if (!head) {
    // If the list is empty, both head and tail point to the new node
    head = tail = newNode;
    newNode.next = newNode.prev = newNode; // Circular link
  } else {
    // If the list is not empty, insert the new node at the end
    newNode.prev = tail;
    newNode.next = head;
    tail.next = newNode; // The old tail points to the new node
    head.prev = newNode; // The head's prev points to the new node
    tail = newNode; // Update the tail to the new node
  }
}
```

##### Insert at the beginning of the circular doubly linked list

```javascript
function insertAtHead(data) {
  const newNode = new Node(data);

  if (!head) {
    // If the list is empty, both head and tail point to the new node
    head = tail = newNode;
    newNode.next = newNode.prev = newNode; // Circular link
  } else {
    // Insert at the beginning and update the head
    newNode.next = head;
    newNode.prev = tail;
    tail.next = newNode; // The old tail points to the new node
    head.prev = newNode; // The old head's prev points to the new node
    head = newNode; // Update the head to the new node
  }
}
```

##### Delete a node by value

```javascript
function deleteNode(data) {
  if (!head) {
    console.log("List is empty");
    return;
  }

  let current = head;

  // Traverse the list to find the node with the given value
  do {
    if (current.data === data) {
      if (current === head && current === tail) {
        // If it's the only node in the list
        head = tail = null;
      } else if (current === head) {
        // If it's the head node
        head = current.next;
        tail.next = head; // Update tail's next
        head.prev = tail; // Update head's prev
      } else if (current === tail) {
        // If it's the tail node
        tail = current.prev;
        head.prev = tail; // Update head's prev
        tail.next = head; // Update tail's next
      } else {
        // If it's a middle node
        current.prev.next = current.next;
        current.next.prev = current.prev;
      }
      return;
    }
    current = current.next;
  } while (current !== head);

  console.log("Node not found");
}
```

##### Print the list (forward direction)

```javascript
function printList() {
  if (!head) {
    console.log("List is empty");
    return;
  }

  let current = head;
  let result = [];

  do {
    result.push(current.data);
    current = current.next;
  } while (current !== head);

  console.log(result.join(" <-> "));
}
```

##### Print the list (backward direction)

```javascript
function printListReverse() {
  if (!tail) {
    console.log("List is empty");
    return;
  }

  let current = tail;
  let result = [];

  do {
    result.push(current.data);
    current = current.prev;
  } while (current !== tail);

  console.log(result.join(" <-> "));
}
```

##### Search for a node by value

```javascript
function search(data) {
  if (!head) {
    console.log("List is empty");
    return false;
  }

  let current = head;
  do {
    if (current.data === data) {
      return true;
    }
    current = current.next;
  } while (current !== head);

  return false;
}
```

##### Tests:

```javascript
// Insert elements into the circular doubly linked list
insertAtEnd(10);
insertAtEnd(20);
insertAtEnd(30);
insertAtHead(5);
insertAtHead(0);

// Print the list in forward direction
console.log("Circular Doubly Linked List (Forward):");
printList(); // Output: 0 <-> 5 <-> 10 <-> 20 <-> 30

// Print the list in reverse direction
console.log("\nCircular Doubly Linked List (Backward):");
printListReverse(); // Output: 30 <-> 20 <-> 10 <-> 5 <-> 0

// Search for an element
console.log("\nIs 20 in the list?", search(20)); // Output: true
console.log("Is 100 in the list?", search(100)); // Output: false

// Delete a node
deleteNode(20);
console.log("\nAfter deleting 20:");
printList(); // Output: 0 <-> 5 <-> 10 <-> 30

deleteNode(0);
console.log("\nAfter deleting 0 (head):");
printList(); // Output: 5 <-> 10 <-> 30

deleteNode(30);
console.log("\nAfter deleting 30 (tail):");
printList(); // Output: 5 <-> 10
```

## See Next:
- [Singly Linked List](singly-linkedList.md)
- [Doubly Linked List](doubly-linkedList.md)
- [Circular Linked List](circular-linkedList.md)
