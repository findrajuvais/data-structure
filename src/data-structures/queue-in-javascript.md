# Queue

A queue is a linear data structure that follows the First In First Out (FIFO) principle, meaning the first element added to the queue will be the first one to be removed.

#### Basic Operations:

1. enqueue(element): Adds an element to the end of the queue.
2. dequeue(): Removes and returns the first element in the queue.
3. peek(): Returns the first element in the queue without removing it.
4. isEmpty(): Checks if the queue is empty.
5. size(): Returns the number of elements in the queue.
6. clear(): Clears all elements from the queue.
7. print(): Displays the queue for debugging purposes.

#### Queue Implementation Using JavaScript Array:

##### Define array:

```javascript
let items = [];
```

##### Check Queue is Empty or not:

```javascript
function isEmpty() {
  return items.length === 0;
}
```

##### Add an element to the end of the queue (enqueue):

```javascript
function enqueue(item) {
  items.push(item);
}
```

##### Remove an element from the front of the queue (dequeue):

```javascript
function dequeue() {
  if (isEmpty()) {
    return "Queue is empty";
  }
  return items.shift();
}
```

##### Peek at the front element of the queue without removing it:

```javascript
function peek() {
  if (isEmpty()) {
    return "Queue is empty";
  }
  return items[0];
}
```

##### Get the size of the queue:

```javascript
function size() {
  return items.length;
}
```

##### Clear the queue:

```javascript
function clear() {
  items = [];
}
```

##### Print the queue:

```javascript
function print() {
  console.log(items.toString());
}

//Tests:
enqueue(10);
enqueue(20);
enqueue(30);

console.log(dequeue()); // 10
console.log(peek()); // 20
console.log(size()); // 2
print(); // 20,30
```

#### Queue Implementation Using Linked List:

##### Implement Linked List Node:

```javascript
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}
```

##### Define variables:

```javascript
let front = null;
let rear = null;
let size = 0;
```

##### Add an element to the queue:

```javascript
function enqueue(value) {
  const newNode = new Node(value);
  if (rear) {
    rear.next = newNode;
  } else {
    front = newNode;
  }
  rear = newNode;
  size++;
}
```

##### Remove an element from the queue:

```javascript
function dequeue() {
  if (isEmpty()) {
    return "Queue is empty";
  }
  const dequeuedValue = front.value;
  front = front.next;
  if (!front) {
    rear = null;
  }
  size--;
  return dequeuedValue;
}
```

##### Peek at the front element without removing it:

```javascript
function peek() {
  if (isEmpty()) {
    return "Queue is empty";
  }
  return front.value;
}
```

##### Check if the queue is empty:

```javascript
function isEmpty() {
  return size === 0;
}
```

##### Get the size of the queue:

```javascript
function size() {
  return size;
}
```

##### Print the queue:

```javascript
function print() {
  let current = front;
  let result = "";
  while (current) {
    result += current.value + " ";
    current = current.next;
  }
  console.log(result.trim());
}

//Tests:
enqueue(10);
enqueue(20);
enqueue(30);

console.log(dequeue()); // 10
console.log(peek()); // 20
print(); // 20,30
```

#### Application of Queue:

1. Job scheduling (e.g., CPU scheduling, print spooling).
2. Graph algorithms (e.g., BFS for traversal).
3. Data streaming (e.g., message queues like RabbitMQ).
4. Background task handling (e.g., email notifications, file processing).
5. Network traffic management (e.g., routers, network buffers).
6. Handling concurrent requests (e.g., web servers, API gateways).
7. Customer support systems (e.g., call center queues).
8. Simulation modeling (e.g., manufacturing, queuing theory in service models).
9. Rate limiting and load balancing.
10. Real-time event processing (e.g., event-driven systems).
