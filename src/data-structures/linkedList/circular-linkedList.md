# LinkedList (Circular Linked List):

    A Circular Linked List is a variation of the linked list where the last node points back to the first node instead of null. This creates a loop in the list, making it circular.

#### Key Characteristics of a Circular Linked List:

1. Circular: The last node points to the first node.
2. Head and Tail: It can have a head (or start) pointer, and in some implementations, a tail pointer which points to the last node and may help in certain operations (like insertion at the end).
3. No Null at End: The next pointer of the last node refers back to the head node.

##### Node class to represent each node in the linked list:

```javascript
class Node {
  constructor(data) {
    this.data = data; // The value of the node
    this.next = null; // Pointer to the next node
  }
}
```

##### Represent LinkedList:

```javascript
let head = null; // A reference to the first node.
let tail = null; // A reference to the last node.
let size = 0; // the number of the node lists.
```

##### Insert at the end of the circular list

```javascript
function insertAtEnd(data) {
  const newNode = new Node(data);

  if (!head) {
    // If the list is empty, create the circular link
    head = tail = newNode;
    newNode.next = head;
  } else {
    // If the list is not empty, insert at the end and adjust the tail's next
    tail.next = newNode;
    tail = newNode;
    tail.next = head; // Maintain circular link
  }
}
```

##### Insert at the beginning of the circular list

```javascript
function insertAtHead(data) {
  const newNode = new Node(data);

  if (!head) {
    // If the list is empty, create the circular link
    head = tail = newNode;
    newNode.next = head;
  } else {
    // Insert new node and adjust pointers
    newNode.next = head;
    head = newNode;
    tail.next = head; // Maintain circular link
  }
}
```

##### Print the list by traversing from the head node

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

  console.log(result.join(" -> "));
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
  let previous = null;

  // Check if the node to be deleted is the head node
  if (current.data === data) {
    if (current === head && current === tail) {
      // Only one node in the list
      head = tail = null;
    } else {
      // Move head pointer and adjust tail
      head = current.next;
      tail.next = head; // Maintain circular link
    }
    return;
  }

  // Traverse to find the node to delete
  do {
    previous = current;
    current = current.next;
    if (current.data === data) {
      // Remove the node
      previous.next = current.next;
      if (current === tail) {
        tail = previous; // Update tail if needed
      }
      return;
    }
  } while (current !== head);

  console.log("Node not found");
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
// Insert elements into the circular linked list
insertAtEnd(10);
insertAtEnd(20);
insertAtEnd(30);
insertAtHead(5);
insertAtHead(0);

// Print the list
console.log("Circular Linked List:");
printList(); // Output: 0 -> 5 -> 10 -> 20 -> 30

// Search for an element
console.log("\nIs 20 in the list?", search(20)); // Output: true
console.log("Is 100 in the list?", search(100)); // Output: false

// Delete a node
deleteNode(20);
console.log("\nAfter deleting 20:");
printList(); // Output: 0 -> 5 -> 10 -> 30

deleteNode(0);
console.log("\nAfter deleting 0 (head):");
printList(); // Output: 5 -> 10 -> 30

deleteNode(30);
console.log("\nAfter deleting 30 (tail):");
printList(); // Output: 5 -> 10
```

## See Next:

- [Circular Linked List](circular-linkedList.md)
- [Circular Doubly Linked List](circular-doubly-linkedList.md)
