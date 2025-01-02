# Priority Queue:

A Priority Queue is a data structure where each element is associated with a priority. Elements are dequeued in order of their priority, meaning that elements with higher priority are dequeued before those with lower priority.

### Implementation:

##### Define maxHeap:

```javascript
let maxHeap = new MaxHeap();
```

##### Insert a new element with a priority into the priority queue:

```javascript
function enqueue(value) {
    maxHeap.insert(value);
}
```

##### Remove and return the highest priority element:

```javascript
function dequeue() {
    return maxHeap.extractMax();
}
```

##### Peek at the highest priority element:

```javascript
function peek() {
    return maxHeap.peek();
}
```

##### Get the size of the priority queue:

```javascript
function size() {
    return maxHeap.size();
}
```

##### Check if the priority queue is empty:

```javascript
function isEmpty() {
    return maxHeap.size() === 0;
}

```

##### Max-heap Priority queue tests:
```javascript
// Enqueue elements with priorities
enqueue(10);
enqueue(20);
enqueue(5);
enqueue(30);

console.log(peek()); // 30 (highest priority)
console.log(dequeue()); // 30 (dequeue highest priority)
console.log(peek()); // 20 (new highest priority)
console.log(size()); // 3 (priority queue size)
```

#### Min-Priority Queue Implementation:

##### Define mapHeap:


```javascript
let minHeap = new MinHeap();
```

##### Min-heap Priority queue tests:
```javascript
// Enqueue elements with priorities
enqueue(10);
enqueue(20);
enqueue(5);
enqueue(30);

console.log(peek()); // 5 (highest priority)
console.log(dequeue()); // 5 (dequeue highest priority)
console.log(peek()); // 10 (new highest priority)
console.log(size()); // 3 (priority queue size)
```

### Next:
- [Heaps Implementation](heaps-in-javascript.md)


