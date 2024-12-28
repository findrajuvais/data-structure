# LinkedList

### Circular Linked List:
    - A Circular Linked List is a variation of the linked list where the last node points back to the first node instead of null. This creates a loop in the list, making it circular.

#### Key Characteristics of a Circular Linked List:
1. Circular: The last node points to the first node.
2. Head and Tail: It can have a head (or start) pointer, and in some implementations, a tail pointer which points to the last node and may help in certain operations (like insertion at the end).
3. No Null at End: The next pointer of the last node refers back to the head node.

##### Node class to represent each node in the linked list:

```javascript
class Node {
  constructor(data) {
    this.data = data;  // The value of the node
    this.next = null;   // Pointer to the next node
  }
}
```